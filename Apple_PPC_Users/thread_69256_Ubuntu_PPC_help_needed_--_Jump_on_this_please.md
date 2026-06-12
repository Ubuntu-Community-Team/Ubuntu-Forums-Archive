---
title: "Ubuntu PPC help needed -- Jump on this please"
date: 2005-09-26
forum: Apple PPC Users
---

### Post by andrewd on 2005-09-26
Hi, first time user of Ubuntu, been watching the project for a while and didn't know there was a PPC version until the other Mac tech at work showed me. For now, all our Mac OS CDs are dead and I've gone to using Ubuntu on the iMac. It's booting so slow and the response times from the system are at best, horrible. I can't get any applications to open and the desktop takes about 15 to complete loading and tell me there are updates available. I need help with this thing because I'm bout ready to toss my iMac out the freakin' window and just stick with my Windows PC. We recently had to yank out the original 40gb drive because it was failing, and replaced it with a 20 that we had lying around that works perfectly. I also put in another 256mb of SD 133Mhz to see if that would help and while it cut the loading time down from 25-35 minutes, it's still unable to run anything. Like I mentioned before, I'm fed up and bout ready to kill it.

---

### Post by andrewd on 2005-09-26
Just a quick update on the available information. I watched the boot and found that the iMac was booting the PowerPC kernel and not the G3 one, which this iMac has... Could that be a definite pointer to problems with the computer booting painfully slow and such?
 
[Edit] I looked at available kernels from the CD, powerpc is the default for PPC, G3, and G4s appearantly, please excuse me for this minor oversight. I'm just trying to get this thing working...
 
[Second Edit] I checked the RAM part numbers out, I'm running 512mb SD PC133 DIMM on 2 sticks, the model number of the iMac is the M5521, the other Mac tech got us Ubuntu 5.1 which we're seeing now as that may be our problem in the first place with my Mac, and not his. We'll get 5.04 and see what happens and if I have more trouble I'll keep posting. Otherwise, this is where I take my leave and apologize for making a foul. *Sits in penalty box*

---

### Post by patrickp on 2005-09-26
hi,

does the mac start the gui ??

if yes then switch to console 1 

login
and type top

then u can see which program takes all the cpu power

if u want to update u must do as root apt-get update
takes a while

and then apt-get upgrade

i hope i could help u to find out where the problem is situated
for a solution i need some more info

patrick

---

### Post by andrewd on 2005-09-26
I get into the GUI, swap back to console 1, and did the TOP command... there's nothing going on besides my TOP from what the computer reports... it looks more like it's just the video card... for some reason... it's reporting that it has the wrong ROM or something like that... I'll have to take another look at it.

---

### Post by patrickp on 2005-09-27
u have to change the videocard driver 

u can do this by editing /etc/X11/xorg.conf

i had the same problem because of the fact that xorg takes a standard ati driver and not the radeon for my powerbook

when u have changed the driver 

u can restart x
and have a look

gl

patrick

---

### Post by andrewd on 2005-09-27
It's reporting "aty128fb: Invalid ROM signature 8181 should be 0xaa55"
and then there's a lot of INSMOD errors... about video card driver modules... vga16fb.ko for one of them... I think this may be the total and utter source of my problems... i'm going to see if i can't find these on the dev CD because i don't want to sit through the GUI all day just to get to 3 webpages...

---

### Post by patrickp on 2005-09-27
hi,


try to use this as your driver in xorg.conf
 
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
Driver "r128"
Option "UseFBDev" "true"
EndSection

if this does not solve the problem

in console 1 do a lspci 
and give me the output

then i can tell u which driver u have to use

cu

patrick

---

