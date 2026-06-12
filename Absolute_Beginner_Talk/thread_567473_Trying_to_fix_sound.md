---
title: "Trying to fix sound"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by cafman on 2007-10-04
I am new to linux and finally got my wireless working.  Next project is the sound.  I am trying to follow the instructions at
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
I'm stuck on the second step where it says Install the linux headers
how do I interpret the  'uname -r' ?
Is uname short for username?  Because I've tried uname, chris (which is my username), etc.   It keeps saying "Can't find package "

---

### Post by maryjanua on 2007-10-04
do you have the sound drivers downloaded to your desktop?

---

### Post by cafman on 2007-10-04
No.
Guess it makes sense I would need drivers though

---

### Post by maryjanua on 2007-10-04
put aplay -l     into a terminal and it will tell you the soundcard

---

### Post by cafman on 2007-10-04
chris@penguin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@penguin:~$ 

Also its a brand new laptop, Compaq presario C500T.  Should I just download the driver from the HP site?

---

### Post by maryjanua on 2007-10-04
if they do a linux driver yeah by all means i would
by the way im no linux guru i just had a problem with intel hdaudio a couple of weeks ago on my first ever linux install and i got help in here to fix it. if i can i'll help u :)

---

### Post by cafman on 2007-10-04
No linux drivers. Only Windows.

---

### Post by maryjanua on 2007-10-04
what kind of soundcard did windows say it was?
i would try conexant

---

### Post by FuturePilot on 2007-10-04
Just put that directly into a terminal
```
sudo apt-get install linux-headers-`uname -r`
```
uname -r is just a way of saying install the linux-headers for the kernel you are currently running.
If you're following that guide the drivers you want are the ALSA drivers
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

---

