---
title: "configure Xorg for 2 different computer"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by quickshade on 2007-12-13
Heres my current problem. For a class I'm taking we are using windows XP and run though a bunch of labs taking pictures (alt-printscreen) of our progress and sending it to our teacher. Since we were only provided Win XP pro and I don't have access to Microsoft word or anything, Also alot of the labs set up profiles and stuff that I don't want to be left on my OS but I don't want to go back and remove them. We also install some testing software and other applications that we only use 2-3 times and then remove them. 

Instead of wasting time with installing windows on my full drive (we are given drives that slide into the top bay on the PC) I decided to install Ubuntu on the drive, and then run Virtual Box with Windows inside that. Since doing this would make it easier to copy files I needed and I could have full access to the PC in case windows needed something I didn't have. So I took my drive home and installed ubuntu and then windows XP inside that (via Virtual Box). Boom, everything works and I can screenshot my entire OS so that I can go back to a new slate with the click of a button or if I don't finish something take a snapshot and come back to it later. 

But now I have a problem, The school computers are dells and my home computer is custom built. So it's a problem getting it to load at the school. The entire OS loads and the loading screen goes away after finishing but then it brings up the login script and just keeps repeating it on screen. If I CTRL-F2 to terminal and login and then try to startx it tries loading the system and brings me to a failed to detect display screen. 

From what I know it's a standard 16-17 inch monitor with an ATI card on the dell, My home setup is a 19 inch HP with Nvidia 7900. (res is 1440*900 on my home, not sure about max on dell) anyways is there any way to configure Xorg to have 2 profiles and me to choose which one I want at boot. BTW I tried the reconfigure Xorg command and got the same screen as before. I've been using Linux for about a year now so I mostly know my way around but this is new for me. Any help would be great, thanks.

---

### Post by Nano Geek on 2007-12-13
Try using the **vesa** driver. It should work on most all hardware.

---

### Post by LowSky on 2007-12-13
vesa driver and use a more standard monitor setting like 1024x768, it will be fine on your wide screen for most stuff for the project

otherwise always boot into recovery mode
and resetup the xorg.conf everytime

---

### Post by quickshade on 2007-12-13
So just boot on my main computer, install the driver and it should boot at the school? Also I just looked it up, says it's made to work with most video cards but it's performance is bad, need I worry? I think I'm going to just install the ATI drivers once I get it running on the dell since I don't need to do labs at home. But just trying to figure out my best option here. Thanks for the quick reply though. I'll try it tomorrow.

---

### Post by Nano Geek on 2007-12-13
> **quickshade said:**
> So just boot on my main computer, install the driver and it should boot at the school? Also I just looked it up, says it's made to work with most video cards but it's performance is bad, need I worry? I think I'm going to just install the ATI drivers once I get it running on the dell since I don't need to do labs at home. But just trying to figure out my best option here. Thanks for the quick reply though. I'll try it tomorrow.Vesa isn't to bad as long as you don't try any type of 3D stuff. But I'd try installing the ATI drivers if that's what the Dells have in them. 

I wish you luck.

---

