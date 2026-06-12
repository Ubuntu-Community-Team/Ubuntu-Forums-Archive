---
title: "Black Screen"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by jermyang on 2007-10-21
Hi, this is a problem that has really been janking me the past half day. I initially used the livecd to try to install gutsy gibbon with windows xp, however, whenever i attempted to "run or install ubuntu" it would go black and my monitor would go into standby, and my keyboard's lock lights would flash repeatedly. I then decided to use the alternate install and everything went off without a hitch: partitioning, installation, it all went fine. But when i tried to go into ubuntu from the dual boot, it would repeat its previous behavior (I did expect it, but was hoping with all my heart that it wouldn't). I was wondering if there were any solutions to this problem?


i am also a true neophyte at this computer stuff and the like, so i would appreciate the use of layman's terms when explaining to my utterly incapable self.

i'm running 
amd athlon64 3200+
ati radeon x800 pro (i've inferred that this could be a problem)

---

### Post by orange2k on 2007-10-21
> **jermyang said:**
> Hi, this is a problem that has really been janking me the past half day. I initially used the livecd to try to install gutsy gibbon with windows xp, however, whenever i attempted to "run or install ubuntu" it would go black and my monitor would go into standby, and my keyboard's lock lights would flash repeatedly. I then decided to use the alternate install and everything went off without a hitch: partitioning, installation, it all went fine. But when i tried to go into ubuntu from the dual boot, it would repeat its previous behavior (I did expect it, but was hoping with all my heart that it wouldn't). I was wondering if there were any solutions to this problem?


i am also a true neophyte at this computer stuff and the like, so i would appreciate the use of layman's terms when explaining to my utterly incapable self.

i'm running 
amd athlon64 3200+
ati radeon x800 pro (i've inferred that this could be a problem)

I have the same problem. It seems to be a known bug in Gutsy.

There is a workaround, though:edit your /boot/grub/menu.lst
and somewhere in the middle of the text file change "quiet splash" to "quiet"...
You will get no graphical splash and no progress bar, but instead you will get a textual screen just like in the older Ubuntu releases. 

I am not very happy about that, because it worked so nice on 7.04 and I`m wondering why they went to fix something that wasn`t broken...
Hopefully this will be fixed in some future update...

---

### Post by rahimveron on 2007-10-21
I had the same prob as it would boot then grub would load and then the screen goes blank until i had Ubuntu login screen. I changed the resolution to 1024*800 and got my Orange ubuntu progress bar back!!!

---

### Post by jit.sd on 2007-10-21
Hey , 
I have the EXACT same problem . Although in windows my screen resolution is set to 1280x800 . Am gonna give that editing the /boot/grub/menu.lst thing a try . hope thata helps .

---

### Post by illuminaris on 2007-10-21
I'm having a similar problem. After I updated to Gutsy Gibbon (7.10) I started getting a black screen on startup. The orange loading bar will come up, then the black screen. It never gets to the login screen. Instead, it goes to what I can only guess is a default mode "low graphics mode". I've been running Linux in this "low graphics mode" ever since. My resolution in usplash.conf is 1024x800 I have no idea what my refresh rate is or where I would go to check/edit that. I'm relatively new to Linux and I'm no programmer.

I tried editing the "quiet splash" and changing it to "quiet" but that didn't work. Please help.

I am running an ATI Radeon 9800 Pro and I have ATI Accelerated graphics driver enabled in Restricted Drivers. My system is 32 bit.

---

