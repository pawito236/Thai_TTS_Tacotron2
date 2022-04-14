# Thai TTS with Tacotron2  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1k4UZ5fk3-6lHbXjnaZ2urJ9UvUGTeyNP?usp=sharing)
 Using [Tacotron2](https://github.com/NVIDIA/tacotron2) and [phoneme](https://medium.com/@pawito236/thai-g2p-seq-to-seq-a1eb96c3be18) as input
 
 ประกอบด้วย Network 2 ส่วนหลัก ๆ คือ
 1. Spectrogram Prediction Network (RNN, Attention, CNN) ทำหน้าที่ในการแปลงข้อมูลจาก sequence of character เป็น mel-spectrogram
 2. WaveNet Vocoder ทำหน้าที่แปลงข้อมูลจาก mel-spectrogram เป็น waveform

![tacotron2_diagram](https://user-images.githubusercontent.com/44425803/163366868-1b4bcfec-4057-4b6a-85d5-57657b42b41a.png)

## Why using phoneme as Input ?
สำหรับโมเดลเสียง tacotron2 การใช้ phoneme แทน wordseg จะช่วยแก้ปัญหาการอ่านผิด ๆ ถูก ๆ ที่เคยเกิดขึ้น ยิ่งไปกว่านั้น จำนวน unique word จะลดลง ซึ่งจะช่วยให้ node network ลดลงด้วย
ทั้งนี้ เวลา Inference เราก็ต้องส่ง phoneme เข้าไป แทนที่จะเป็นประโยคหรือเป็นคำ ซึ่งอาจจะเพิ่มความยุ่งยากในการแปลงเป็น phoneme เอาเข้าโมเดล แต่ก็เป็นการ Trade-off ระหว่าง preprocess กับ คุณภาพการอ่านที่ดีขึ้น

## Training G2P seq-to-seq model
[Train G2P seq-to-seq](https://medium.com/@pawito236/thai-g2p-seq-to-seq-a1eb96c3be18)  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1qmJMbBn0Yp0-Sakej3ADDdWZKVmINCfY?usp=sharing)

G2P คือการแปลงข้อความจากตัวเขียน เช่น “ฉัน รัก เธอ” → สัทอักษร (Phoneme) หรือ อักษรที่ใช้กำหนดแทนเสียงนั่นเอง โดย Tool ที่จะนำเสนอให้ลองใช้นั้นคือ [cmusphinx](https://github.com/cmusphinx/g2p-seq2seq)

## References and Related repos
[Thai_TTS](https://github.com/Prim9000/Thai_TTS) Thai TTS Tacotron is the text to speech model in Thai trained by [Tacotron2.](https://github.com/NVIDIA/tacotron2)

[Thai Text To Speech with Tacotron2 | Lifelike Speech Synthesis](https://prim9000.medium.com/lifelike-speech-synthesis-thai-text-to-speech-with-tacotron2-24460af0b33e)

[Tacotron2 Thai TTS](https://medium.com/nectec/tacotron2-thai-tts-b5d26a015465)

[Introduction to Tacotron 2 : End-to-End Text to Speech และตัวอย่างภาษาไทย](https://insight.avantis.finance/tacotron-2-%E0%B8%8A%E0%B8%B4%E0%B8%94%E0%B9%83%E0%B8%99%E0%B9%80%E0%B8%A5%E0%B8%A2%E0%B9%80%E0%B8%9E%E0%B9%88-9c35fb6a6227)

## license
NECTEC licensed TSync2 under CC-BY-NC-SA

## Medium
[Thai TTS with Tacotron 2](https://medium.com/@pawito236/tacotron-2-thai-tts-with-phoneme-82264fd71549)
