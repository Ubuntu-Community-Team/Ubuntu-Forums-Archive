---
title: "Only able to run in failsafe"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by Newbot on 2005-10-25
If I boot into failsafe then I can start gdm and everything will be fine (Other then being able to only have the console with X running and not anyother...) but if I boot into Ubuntu normally then X will start and run for a few seconds then crash. If I am using failsafe and I switch the runlevel to 2,3, or 5 then it will do the same thing that booting normally will do.

System config in case it matters:
Ubuntu version: Breezy Badger 32 bit edition
Video Card: Nvidia 6600GT pci-e
Processor: AMD athlon 3000 64
RAM: 512

---

### Post by Dr. Nick on 2005-10-25
Any specific errors?, have you tried to change nvidia back to nv in your xorg.conf. Not sure if that would cause a crash or affect failsafe.

Also what type of video card? pci,agp, or pci express, I noticed your busid seems different than im used to seeing.

---

### Post by BatsotO on 2005-10-25
Was the error saying something like " your session only last for 10 seconds..." ?
if so there should be notice to check some log file, I forgot what log file. I was run in to this error before,  look in to the log file and found lynx cause the error, re install lynx and everything back to normal.

---

### Post by az on 2005-10-25
Try

sudo apt-get -f install, to see if there are any packages that are not properly installed.

---

### Post by Newbot on 2005-10-25
> 
Any specific errors?, have you tried to change nvidia back to nv in your xorg.conf. Not sure if that would cause a crash or affect failsafe.

Also what type of video card? pci,agp, or pci express, I noticed your busid seems different than im used to seeing.

Where would I look to find errors? Nothing popped up in front of me.  Switching to the nv drivers didn't help, it was doing that before I installed the nvidia ones anyways, I was hoping by doing that it would help (Obviously it didn't).
I have a pci express.

> 

Try

sudo apt-get -f install, to see if there are any packages that are not properly installed.

Nope, packages seemed to be fine.

---

### Post by Dr. Nick on 2005-10-26
[QUOTE=Newbot]Where would I look to find errors? Nothing popped up in front of me.  Switching to the nv drivers didn't help, it was doing that before I installed the nvidia ones anyways, I was hoping by doing that it would help (Obviously it didn't).
I have a pci express.
[/QUOTE]

I see the pci express in your origional post now :rolleyes: 

Look in /var/log/xorg.0.log file and look toward the botom for errors
you may also look at the one that has a .old extension aswell for errors. 

Ive never seen it happen before.
Have you tried  sudo dpkg-reconfigure xserver-xorg ?My not work but maybe wirth a shot

---

