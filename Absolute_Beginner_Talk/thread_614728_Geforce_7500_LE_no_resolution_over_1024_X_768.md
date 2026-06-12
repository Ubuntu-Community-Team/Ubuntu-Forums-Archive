---
title: "Geforce 7500 LE no resolution over 1024 X 768"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by vorostatz on 2007-11-16
Ok first off let me say to anyone who can help me a million thank yous in advance, that being said please respond in the most basic terms possible, I am a complete NEWBIE.

I have a 7500 LE geforce, and I have it connected to a 32 inch toshiba TV via DVI.  I cant get resolution over 1024 X 768 which sucks big time because the gorgeous ubuntu interface (which I am dying to use) is cut off at the top and bottom.  I have enabled the restricted driver but I am still unable to get a resolution over 1024 X 768

I would love to have a 1824 X 1028 resolution 
or a 1680x1050

heck or even a 1400 X 1050

Anything so I can see the whole interface (because damn it looks good)

I have downloaded Nvidia drivers from the website (both the 64 bit and 32 bit linux drivers) but the intructions they give me to install dont work (please remember right now I am an uneducated windows user), I dont even know if these are different from the restricted drivers I enabled for Ubuntu.

Any help would be greatly appreciated

---

### Post by markyb86 on 2007-11-16
if you have the restricted drivers in do this at the console

> sudo nvidia-glx-config enable
and then
> sudo nvidia-settings

worked for me but im only using a 19inch widescreen on the nvidia geforce 6150 LE

---

### Post by vorostatz on 2007-11-16
:) thanks I will definitely give this a try tonight

---

### Post by stchman on 2007-11-16
> **vorostatz said:**
> Ok first off let me say to anyone who can help me a million thank yous in advance, that being said please respond in the most basic terms possible, I am a complete NEWBIE.

I have a 7500 LE geforce, and I have it connected to a 32 inch toshiba TV via DVI.  I cant get resolution over 1024 X 768 which sucks big time because the gorgeous ubuntu interface (which I am dying to use) is cut off at the top and bottom.  I have enabled the restricted driver but I am still unable to get a resolution over 1024 X 768

I would love to have a 1824 X 1028 resolution 
or a 1680x1050

heck or even a 1400 X 1050

Anything so I can see the whole interface (because damn it looks good)

I have downloaded Nvidia drivers from the website (both the 64 bit and 32 bit linux drivers) but the intructions they give me to install dont work (please remember right now I am an uneducated windows user), I dont even know if these are different from the restricted drivers I enabled for Ubuntu.

Any help would be greatly appreciated

I am going to gather you are running Gutsy?  When I installed Feisty I had a similar problem and I fixed it via this way.

gksudo gedit /etc/X11/xorg.conf

I added "1280x1024" as the first res in the line of resolutions and re-booted.  I was then able to get the desired resolution.

What is the native resolution of the Toshiba TV?  Is it an HDTV (LCD probably)?  If so the 32 inch ones usually have a native resolution of either 1280x720 or 1366x768.  There are some quote HDTVs that have a native res of 1024x768.

---

