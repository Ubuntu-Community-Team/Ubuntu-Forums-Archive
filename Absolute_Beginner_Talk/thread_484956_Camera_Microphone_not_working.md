---
title: "Camera Microphone not working"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by JrkG on 2007-06-26
Hi.
I'm using Logitech QuickCam Messenger. On Ubuntu 6.10 the mic was working fine but after upgrade to 7.04 it has gone from devices list in ALSA mixer.
here is my lsusb
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 046d:08f6 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:7104 Hewlett-Packard DeskJet 3420c
Bus 001 Device 003: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 001 Device 001: ID 0000:0000 
```

Please help. My mainboard has dead mic input. It's my only way to use Skype.

JrkG

---

### Post by xdarkxanarchyx on 2007-07-17
I'm having the same problem >_>
```
 Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
```

---

### Post by Super TWiT on 2007-07-17
Does the device show up in the preferences dialog in Alsa mixer?

---

### Post by xdarkxanarchyx on 2007-07-17
No, does anyone know how to make Ubuntu recognize the microphone part again? It worked fine in 6.10 the camera didn't work then... now the camera works but the mic doesn't. lol ](*,)

---

### Post by JrkG on 2007-07-24
No, In 6.10 both camera and microphone were working. Now in Feisty I have no camera device in ALSA and no picture. 
JrkG

---

### Post by MaximB on 2007-08-13
I have the same problem, can someone help ?
and I have been looking in about 20 similar threads.

---

### Post by xdarkxanarchyx on 2007-08-21
I got it to sort of work on Debian Unstable on a Dell Dimension 2350 after I compiled the 2.6.23-rc2 kernel but it was incomprehensible and slightly distorted.

---

### Post by xdarkxanarchyx on 2008-01-08
Update:
Updated to Gutsy  from repo's and everything's working great. :D

---

### Post by philinux on 2008-01-08
I have the same camera. I'm stuck with no mic can you tell me what you did. Here's my lsusb

 lsusb
Bus 001 Device 003: ID 046d:08da Logitech, Inc. 
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000 

The camera works fine but no sound from mic.

Whats your lsusb look like too.

---

