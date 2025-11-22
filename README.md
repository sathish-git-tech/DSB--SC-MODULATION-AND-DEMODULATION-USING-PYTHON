# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message
   
   __program__:
```
import numpy as np
import matplotlib.pyplot as plt
Am = 6.2
fm = 494
Ac = 12.4
fc = 4940
fs = 49400
t = np.arange(0, 3/fm, 1/fs)
m1 = Am * np.cos(2 * np.pi * fm * t)
m2 = Am * np.cos(1.57 - 2 * np.pi * fm * t)
c1 = Ac * np.cos(2 * np.pi * fc * t)
c2 = Ac * np.cos(1.57 - 2 * np.pi * fc * t)
s1 = c1 * m1
s2 = c2 * m2
Slsb = s1 + s2
Susb = s1 - s2
plt.figure(figsize=(10, 8))
plt.subplot(4, 1, 1)
plt.plot(t, m1)
plt.subplot(4, 1, 2)
plt.plot(t, c1)
plt.subplot(4, 1, 3)
plt.plot(t, Slsb)
plt.subplot(4, 1, 4)
plt.plot(t, Susb)
plt.tight_layout()
plt.show()
```
  __Tabulation__:
<img width="1033" height="1280" alt="image" src="https://github.com/user-attachments/assets/60895adc-f54c-47b5-abd5-5b470515943c" />

   __Output__:
<img width="1189" height="889" alt="image" src="https://github.com/user-attachments/assets/b3e90ec6-a031-49b4-b8c6-0bf84e07c092" />

   __Result__:
Thus the DSB-SC is proved and verified using python successfully.
