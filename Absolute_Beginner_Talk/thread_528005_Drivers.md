---
title: "Drivers?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by saximus on 2007-08-17
Hello,

I have installed ubuntu studio and finally managed to get it working - I love it - but I have one problem.. I have noticed that the sound quality is not very good when playing music and also that many of the audio programs do not work.. I get the impression that programs using MIDI work fine, but those prcessing .wav does not work. 

Another problem is that video can be played easily, but I'm having trouble running complex screen-savers for example.. These seem to be too heavy for my system. 

It seems to me like some of my components are not working properly - I've got a 256mb ATI radeon graphics card and a Realtec AC97 sound card. Not top of the line stuff, but they should be able to run simple tasks in ubuntu right? 

I'm wondering if something is wrong with the drivers..

A point worth mentioning is that I had to use the  command -irqpoll to get ubuntu studio working at all - could this be a part of the problem? 

Hope that someone can help me out here! I can't live without proper sound quality;)

---

### Post by skymera on 2007-08-17
ypu proberly have old drivers.
im not a driver extpert but i suggest looking for updated drivers

---

### Post by overdrank on 2007-08-17
> **saximus said:**
> Hello,

I have installed ubuntu studio and finally managed to get it working - I love it - but I have one problem.. I have noticed that the sound quality is not very good when playing music and also that many of the audio programs do not work.. I get the impression that programs using MIDI work fine, but those prcessing .wav does not work. 

Another problem is that video can be played easily, but I'm having trouble running complex screen-savers for example.. These seem to be too heavy for my system. 

It seems to me like some of my components are not working properly - I've got a 256mb ATI radeon graphics card and a Realtec AC97 sound card. Not top of the line stuff, but they should be able to run simple tasks in ubuntu right? 

I'm wondering if something is wrong with the drivers..

A point worth mentioning is that I had to use the  command -irqpoll to get ubuntu studio working at all - could this be a part of the problem? 

Hope that someone can help me out here! I can't live without proper sound quality;)

HI if we new the model of your ATI card that would help but maybe this link will help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
As for your sound maybe this will help
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Good luck!

---

### Post by saximus on 2007-08-18
Hello again,

Thank you for the hints - I tried reinstalling the drivers, but its all the same as before. The sound is horrible. I can hear music playing but especially the bass is all screwed up. 

I can find the following audio and video devices by using the using the command lspci -v

AC'97 Audio Controller
ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]

I recognise these from windows as being the right description for my components. I've downloaded the linux drivers from the websites of the manufacturers, but I don't know how to install them.. I've found the following file for the audio:

realtek-linux-audiopack-4.06a.tar.bz2

I don't care that much about the video driver - I can do that later, but if someone can tell me how I can get the audio driver installed, I would be very greatful! 

Hope for a response:)

---

