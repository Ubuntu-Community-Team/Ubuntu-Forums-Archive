---
title: "eeePC1005HA: Internal USB Camera &amp; microphone not working"
date: 2011-05-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pazb on 2011-05-31
Hi, I seem to be having problems with the integrated USB webcam. 

I wouldn't have thought to check if the cam was working until a friend gave me the link to this interesting interactive website that was light-sensitive. Upon realizing it didn't work, I decided to Google it. 

According to suggestions I found, I downloaded the Cheese Webcam Booth and initially it wasn't displaying any image (the little indicator light flashed for a second before going out.) After some time, I ran Cheese again and it worked. 

After that, it hasn't worked at all. Any suggestions to get it working? I've also tried running it on Skype, but it isn't working on it either. 

The microphone isn't working on Skype, either.

---

### Post by Jouke74 on 2011-07-14
Webcam should work without any problems. Make sure that it is on in your BIOS. 

Add the following to grub default : acpi_osi=Linux.

For the microphone you need to install pavucontrol (mixer for pulse audio). Then open this program, go to the microphone settings and change the stereo volume control to individually regulate left and right. Subsequently move the slider left to 90% and the slider right to 30%. Now it should start working. If not, suspend the system and restart.. (funny enough).

Link: [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

---

### Post by Tiger 955 on 2011-07-29
Thanks Jouke74 your a star! been trying to get microphone to work for ages with Skype (it worked with Sound Recorder OK), changed the settings as suggested & it worked straight away.
Why these settings? How did you find this out? Very strange!!

Thanks again :D

---

