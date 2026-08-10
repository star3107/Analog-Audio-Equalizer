# Design and Development of a 5-Band Analog Audio Equalizer

This repository contains the design, schematic, simulation, and hardware implementation for a **5-Band Analog Audio Equalizer** built using TL064 operational amplifiers. \
The system splits an incoming analog audio signal into five distinct frequency bands using 4th-order Multiple Feedback (MFB) band-pass active filters, 
allows independent gain control per band via potentiometers, and recombines the signals through a summing amplifier stage to drive wired headphones.

---

## Key Features

* **4th-Order Band-Pass Filtering:** Each band uses two cascaded 2nd-order MFB active filter stages to achieve sharp frequency selectivity and minimize inter-band crosstalk.
* **Independent Gain Control:** Integrated potentiometer stages allow dedicated amplification or attenuation across each frequency band.
* **Low-Power Op-Amp Architecture:** Powered by JFET-input TL064 quad operational amplifiers.
* **Custom PCB Implementation:** Complete hardware prototype implemented on a 2-layer printed circuit board.
* **Standard Audio I/O:** 3.5 mm auxiliary audio input and output interfaces for real-time audio processing.

---

## System Architecture

<img width="653" height="557" alt="image" src="https://github.com/user-attachments/assets/a51cbae1-aa4c-460d-879e-7efd43e2e42f" />

1. **Audio Input:** Accepts standard line-level or headphone audio signals via a 3.5 mm TRS stereo audio jack.
2. **Frequency Band Separation:** The input signal is split across five parallel active band-pass filter paths.
3. **Gain Control:** Each band output flows into an active gain control circuit adjusted by a 10 kΩ potentiometer.
4. **Summing Stage:** A TL064-based inverting summing amplifier combines the processed outputs from all five bands.
5. **Audio Output:** The combined analog signal is buffered to drive low-impedance wired earphones.

---

## Target Frequency Bands

The audio spectrum is partitioned into five target bands covering bass, midrange, and treble frequencies:

| Band | Frequency Range | Spectrum Segment |
| :--- | :--- | :--- |
| **Band 1** | 60 Hz – 300 Hz | Low Bass / Sub-Bass |
| **Band 2** | 300 Hz – 1 kHz | Mid-Bass / Low Midrange |
| **Band 3** | 1 kHz – 4 kHz | Midrange / Vocals |
| **Band 4** | 4 kHz – 10 kHz | High Midrange / Upper Harmonics |
| **Band 5** | 10 kHz – 16 kHz | Treble / Presence |

---

## Verification & Testing Results

### Simulation Analysis
* **Time-Domain:** Simulated using a composite input signal consisting of five combined sine waves (100 Hz, 500 Hz, 2 kHz, 6 kHz, 15 kHz) at 5 mV amplitude each.
* Time-domain plots confirm progressive attenuation of out-of-band components through the 1st and 2nd stage cascaded filters.
<img width="705" height="181" alt="image" src="https://github.com/user-attachments/assets/f19ff6d3-5637-47bc-8bd8-3359402e871a" />

* **Frequency-Domain:** Fast Fourier Transform (FFT) analysis confirms distinct band-pass responses across each targeted frequency window with sharp roll-offs.
<img width="741" height="285" alt="image" src="https://github.com/user-attachments/assets/37624a2f-6341-47f3-bbc3-57199b83cf21" />



### Hardware & Prototype Validation
* **Oscilloscope FFT Analysis:** Hardware validation was performed using an oscilloscope FFT function on audio signals.
* **Gain Response:** Adjusting individual potentiometers resulted in proportional amplitude changes in the FFT spectrum for corresponding bands
*  (e.g., boosting Band 2 produces a distinct spectral magnitude peak between 300 Hz and 1 kHz).

## PCB Prototype
<img width="406" height="357" alt="image" src="https://github.com/user-attachments/assets/68d2717f-71ec-49c2-947f-570f26be7d15" />

## Note
For a detailed Analysis of Filter Design and references please look into Report.pdf file


