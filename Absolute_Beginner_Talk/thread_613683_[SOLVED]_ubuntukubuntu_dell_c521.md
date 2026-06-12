---
title: "[SOLVED] ubuntu/kubuntu dell c521"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by markyb86 on 2007-11-15
I am having a hard time getting either distro to work efficiently. Its the graphics that are the problem. I have an nvidia geforce 6150 le , and a hp w1907 widescreen lcd. 

I cant get any widescreen resolutions to work, they are all in my xorg.conf and i cant seem to get the nvidia drivers to work at all. I have to use vesa or my mouse cursor goes away making it unusable. by the way no matter what i set up in the dpkg-reconfigure xserver-xorg, when using nvidia it only gives me 1024x768. and the highest i get on vesa is 1280x1024 and its distorted and stretched.

I need 1440x900 to see the screen correctly. I had the problems with ubuntu 7.10 and kubuntu 7.04

im not a very adept user when it comes to the cli interface. i had no problem installing ubuntu on my p4 with a geforce 5500 and a 17inch crt

please help :-)

---

### Post by overdrank on 2007-11-15
> **markyb86 said:**
> I am having a hard time getting either distro to work efficiently. Its the graphics that are the problem. I have an nvidia geforce 6150 le , and a hp w1907 widescreen lcd. 

I cant get any widescreen resolutions to work, they are all in my xorg.conf and i cant seem to get the nvidia drivers to work at all. I have to use vesa or my mouse cursor goes away making it unusable. by the way no matter what i set up in the dpkg-reconfigure xserver-xorg, when using nvidia it only gives me 1024x768. and the highest i get on vesa is 1280x1024 and its distorted and stretched.

I need 1440x900 to see the screen correctly. I had the problems with ubuntu 7.10 and kubuntu 7.04

im not a very adept user when it comes to the cli interface. i had no problem installing ubuntu on my p4 with a geforce 5500 and a 17inch crt

please help :-)
HI and when you have the nvidia drivers installed you could try the nvidia settings with the command ```
gksudo nvidia-settings
```

---

### Post by markyb86 on 2007-11-15
also could you tell me if i did it right? I downloaded them from the package manager, and then picked them in the display properties in system settings? I dont know if im using the correct terminology im at work using xp.... also should i do this command from a shell when the xserver is started or stopped or does it matter?? sorry if im annoying!!!!!!!!!!!

---

### Post by overdrank on 2007-11-15
> **markyb86 said:**
> also could you tell me if i did it right? I downloaded them from the package manager, and then picked them in the display properties in system settings? I dont know if im using the correct terminology im at work using xp.... also should i do this command from a shell when the xserver is started or stopped or does it matter?? sorry if im annoying!!!!!!!!!!!

HI I would say the restricted drivers located under system, administration. To run the command you can do it from the desktop with the alt,F2 keys. This will bring up a run application window. Good luck!

---

### Post by markyb86 on 2007-11-15
Thank you!! I will post my results after work!! :guitar:

---

### Post by markyb86 on 2007-11-16
It needed a sudo nvidia-glx-config enable

then the sudo nvidia-settings

and this is after i install the regular nvidia-glx. I had legacy installed :-( took me all night to get this far

but works now :-)

---

### Post by overdrank on 2007-11-16
> **markyb86 said:**
> It needed a sudo nvidia-glx-config enable

then the sudo nvidia-settings

and this is after i install the regular nvidia-glx. I had legacy installed :-( took me all night to get this far

but works now :-)

Congrats and good luck! Please mark as solved under thread tools. :guitar:

---

### Post by markyb86 on 2007-11-16
Thank you!

---

