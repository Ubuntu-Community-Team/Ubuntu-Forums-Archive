---
title: "usb webcam and 5.1 speakers on feisty ?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by highenergy on 2007-04-22
Hi,

I have a couple of questions. First, does feisty supports usb webcams? And second does feisty supports 5.1 speakers?

best regards
H.E.

---

### Post by chemtut on 2007-04-22
it certainly supports webcams-! use a cheap one from Tesco(UK) and I use the progam  "camorama"----use search in synaptic

good luck

---

### Post by highenergy on 2007-04-22
Thank you for your reply chemtut.



I use both fly 1.3 MP webcam a cheap one and orite RN3500 5 MP webcam which is also a cheap one. But I coudn't able to use both webcams to work with Ekiga. I want both of them to work with ekiga and amsn. By the way fly webcam has build-in mic which also works trough usb. I've installed camorama as you said. When I run it it gives me an error which says "Could not connect to video device /dev/video0. Please check connection "


What about 5.1 speakers? I use creative 5.1 speakers. But I am hearing a high frequency noise from center ( bass) speaker when I increase the volume. I also post a bug message to the official also-project page but still there is no answer.


```

ubuntu@ubuntu:~$ lsusb
Bus 005 Device 004: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05a9:4519 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000 

```

regards
H.E.

---

### Post by highenergy on 2007-04-23
Anyway, I've looked for similar posts on the forum and finally found a way out. There is a software for ubuntu called EasyCam which installs drivers for you. haha :popcorn: 

```

05a9:4519 OmniVision Technologies, Inc. 

```

it's my webcam and it's supported by EasyCam.
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

