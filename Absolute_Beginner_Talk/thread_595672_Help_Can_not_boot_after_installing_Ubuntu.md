---
title: "Help: Can not boot after installing Ubuntu"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by vtmn215 on 2007-10-29
Hello guys!  I decided to try out 7.1 on my dell xps 1210 but, I got big problems now...  I thought I installed it.  Followed the steps using the guided partitioning tool to dual boot but now, I cannot book into anything.  I have no idea what I did wrong.  I am so new at this that I don't even know how to explain my problem correctly. :confused::confused::confused::confused:  I hope someone is nice enough to guide me though this.  I think I am going to restore my system to factory specs with vista now since my notebook right now is a door stop.

---

### Post by bodhi.zazen on 2007-10-29
What happens when you try to boot ?

---

### Post by vtmn215 on 2007-10-29
> **bodhi.zazen said:**
> What happens when you try to boot ?

Upon bootup, my notebook beeps and says "No bootable devices--strike F1 to retry boot, F2 for setup utility Press F5 to run onboard diagnostics.

---

### Post by kvizz on 2007-10-29
i think it's the problem of BIOS settings. Your hard drive is not mentioned as bootable device. Strike F2 and correct your settings in the setup utility.

---

### Post by vtmn215 on 2007-10-29
> **kvizz said:**
> i think it's the problem of BIOS settings. Your hard drive is not mentioned as bootable device. Strike F2 and correct your settings in the setup utility.

I set the hdd as the first boot device but I still get the same problem

---

### Post by vtmn215 on 2007-10-29
When I try to reinstall ubuntu, i don't know how to install it onto the partition that I initially made for ubuntu. When i get to the partition section, the guided bullet pushes me to the part with vista. When i go to the manual section and pick the partition i made for ubuntu, it says "No root file system is defined. Please correct this from the partitioning menu." I don't know what to do at that point. I guess i am gonna go for the complete wipe and install ubunu. Man, talk about getting tossed into the deep end of the pool with no floaties

---

### Post by Sef on 2007-10-29
> When i go to the manual section and pick the partition i made for ubuntu, it says "No root file system is defined. Please correct this from the partitioning menu." I don't know what to do at that point

When manual partitioning, you need to set one partition as root (usually the first one you do.)  To set it as root, make sure that it is set to /.

---

### Post by mds06 on 2007-10-29
put a "/" as to define the root partition i think it might be something like /media right now..... see if that helps also you will need a swap paritition...

---

### Post by vtmn215 on 2007-10-29
well, i chose the path of no return lol! I am formatting the whole drive for ubuntu. I guess it cant be any worse than vista.... Vista is not good

---

### Post by vtmn215 on 2007-10-29
well I got ubuntu running on my dell xps m1210 but for some reason, i cannot get my webcam or my video card to work.

---

