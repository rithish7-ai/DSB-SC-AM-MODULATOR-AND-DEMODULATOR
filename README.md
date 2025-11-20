# DSB-SC-AM-MODULATOR-AND-DEMODULATOR
## AIM:
To write a program to perform DSBSC modulation and demodulation using SCI LAB and study its spectral characteristics

## EQUIPMENTS REQUIRED
•	Computer with i3 Processor 
•	SCI LAB

Note: Keep all the switch faults in off position

## ALGORITHM:

1.	Define Parameters:
   
    •	Fs: Sampling frequency.
    
    •	T: Duration of the signal.
    
    •	Fc: Carrier frequency.
    
    •	Fm: Frequency of the message signal.
    
    •	Amplitude: Maximum amplitude of the message signal.

2.	Generate Signals:
 
  •	Message Signal: A sinusoidal signal that will be modulated.
  
  •	Carrier Signal: A high-frequency sinusoidal signal used for modulation.

3.	DSBSC Modulation:
   
  •	Modulated Signal: Multiply the message signal by the carrier signal to produce the DSBSC signal.

4.	DSBSC Demodulation:

  •	Multiplication: Multiply the modulated signal by the carrier signal to get the product of the message signal with itself (i.e., the original message signal plus high-frequency components).

  •	Low-pass Filtering: Apply a Butterworth low-pass filter to remove the high- frequency components and recover the original message signal.

5.	Visualization:
   
  Plot the message signal, carrier signal, DSBSC modulated signal, and the recovered signal after demodulation.

## PROCEDURE

  •	Refer Algorithms and write code for the experiment.
  
  •	Open SCILAB in System
  
  •	Type your code in New Editor
  
  •	Save the file
   
  •	Execute the code
  
  •	If any Error, correct it in code and execute again
  
  •	Verify the generated waveform using Tabulation and Model Waveform
  
## MODEL GRAPH:
<img width="503" height="479" alt="image" src="https://github.com/user-attachments/assets/9f4fdea5-8f1d-44ae-a75a-8c3737088c0a" />

## PROGRAM:

clc;

clear;

close();

am = 7.5;  

ac = 15; 

fm =217.9; 

fc = 2179; 

fs = 21790;       


t = 0:1/fs:2/fm;

N = length(t);

m = am * cos(2 * %pi * fm * t);

c = ac * cos(2 * %pi * fc * t);

s = (ac + m) .* cos(2 * %pi * fc * t);

v = s .* cos(2 * %pi * fc * t); 

cutoff = 2 * fm;      

k = 0:N-1;

freq = k * (fs / N);

freq(freq > fs/2) = freq(freq > fs/2) - fs; 

V = fft(v);          

mask = abs(freq) <= cutoff; 

Vf = V .* mask;           

vlp = real(ifft(Vf));            

demod = 2 * (vlp - ac/2);

demod = demod - mean(demod) + mean(m); 

scf(0);

subplot(4,1,1);

plot(t, m);

xtitle("Message m(t)", "Time (s)", "Amplitude");

subplot(4,1,2);

plot(t, c);

xtitle("Carrier c(t)", "Time (s)", "Amplitude");

subplot(4,1,3);

plot(t, s);

xtitle("AM s(t)", "Time (s)", "Amplitude");

subplot(4,1,4);

plot(t, demod);

xtitle("Demodulated (Coherent) signal", "Time (s)", "Amplitude");


## TABULATION:
<img width="325" height="360" alt="image" src="https://github.com/user-attachments/assets/a6fb8ec1-6782-4697-b0d1-2efab22920bb" />


## OUTPUT:
<img width="676" height="576" alt="image" src="https://github.com/user-attachments/assets/d9fd4db4-f781-46af-9847-25b6a8301616" />



## RESULT:
Thus the DSB-SC-AM Modulation and Demodulation is generated.
