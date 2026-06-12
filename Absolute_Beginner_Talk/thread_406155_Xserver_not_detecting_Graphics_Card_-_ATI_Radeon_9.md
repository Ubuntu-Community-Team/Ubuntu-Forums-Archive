---
title: "Xserver not detecting Graphics Card - ATI Radeon 9250"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by s0me_kid on 2007-04-10
Hi, 

I am a first time Linux/Ubuntu user, long time window user. :)

My problem is this:

I get an error when booting Ubuntu saying that there were no screens found. The Xserver is only detecting the old intergrated graphics on the motherboard and not my ATI Radeon 9250 card, or at least I think. If this is the case, how would I go about getting Ubuntu into booting into the GUI enviroment using my graphic card as the main source of video. 

Thanks for your time in reading and replying (hopefully).

---

### Post by dbbolton on 2007-04-10
are you just booting from the live cd, or have you installed it ?

---

### Post by s0me_kid on 2007-04-10
It's installed, dual booted with Windows XP. Graphics works wonderful with the XP, but not the Ubuntu partition.

---

### Post by dbbolton on 2007-04-10
boot in to recovery mode, and run ```
sudo dpkg-reconfigure xserver-xorg
```

note what driver it chooses, and what graphics card it detects.

---

### Post by Razorback on 2007-04-10
You will need to select the "ati" driver.  I had trouble getting my 9250 to work but the later versions seemed to be more compatible.  You will need to get the "fglrx" driver installed after that if you need 3d if not stay with the ati driver.

---

### Post by heyilikeyoursweater on 2007-04-21
I'm having this same problem. I'm pretty sure I've got fglrx installed, because I can select it when I type 
sudo dpkg-reconfigure xserver-xorgsudo dpkg-reconfigure xserver-xorg I need to know how to find the busID of my graphics card. What do I do?

---

