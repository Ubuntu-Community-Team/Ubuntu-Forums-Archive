---
title: "Ubuntu not installing"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Atomfix on 2007-08-18
Hey, i have been trying to install Ubuntu on my laptop all day, it is a "Dell Latitude C600", iv'e ordered 3 CD's and they all have the same problem installing on my system. When i insert the CD it comes up with a menu, i have press "start or install Ubuntu" then it does the kernel loading etc etc then it comes up with the ubuntu splash screen, but it does nothing for 3 minutes then the whole screen comes black with a _ flashing in the right cornor, then in the next 1 minute it comes up with this

[ 202.74800] Buffer I/O error on device fd0, logical block 0

then nothing else after that, does anyone know what im supposed to do?, am i totaly supposed to format the system? am i supposed to change something in the MBR? or something? i have tryed that wubi thingy which downloads ubuntu and installs it but that caused more proberlems now becuase win XP and ubuntu is not loading, it just restarts all the time.

---

### Post by mysticmatrix on 2007-08-18
Looking at specs of your laptop, that seems to have only 128 MB of ram. In such a case, the live graphical installer CD won't work(It requires 256 MB atleast) , and you would need the alternate install CD to install Ubuntu.

---

### Post by Atomfix on 2007-08-18
iv'e got 256MB of RAM, and i dno what CD's they are but it says in black writeing on the discs that they are "Ubuntu 7.04 for your PC" only, it doesent say live or install on it, but it does have the option of isntalling in the menu on bootup

---

### Post by oilchangeguy on 2007-08-18
> **Atomfix said:**
> iv'e got 256MB of RAM, and i dno what CD's they are but it says in black writeing on the discs that they are "Ubuntu 7.04 for your PC" only, it doesent say live or install on it, but it does have the option of isntalling in the menu on bootup

your laptops on board video is taking some of the ram. the computer needs a full 256 to do the install.

---

### Post by sailor2001 on 2007-08-18
are you booting into the disk? (is your bios set to boot to the cdrom?)

---

### Post by overdrank on 2007-08-18
> **oilchangeguy said:**
> your laptops on board video is taking some of the ram. the computer needs a full 256 to do the install.

I agree and you can download the alternate cd here
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Scroll down to the alternate cd and be sure to look at the 
If you need help burning these images to disk, see this guide.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Atomfix on 2007-08-18
the video controller is only taking 8 MB from it, i got ubuntu wokring on my laptop once but it stoped working on reboot and it stoped win XP working too, what has the
[ 202.74800] Buffer I/O error on device fd0, logical block 0
problem gotta do with my RAM anyway? it looks like its related to the hardrive than the RAM

---

### Post by oilchangeguy on 2007-08-18
> **sailor2001 said:**
> are you booting into the disk? (is your bios set to boot to the cdrom?)

read the users first post. they're getting to the start/install option. so the computer is set to boot from the cd drive.

---

### Post by Atomfix on 2007-08-18
its booting from CD perfect and shows the menu O.K, iv'e never had any problems with the hardrive at all, i can reinstall win XP back on there with no problem

---

### Post by Fonon on 2007-08-18
Ubuntu needs the full RAM, so even 8 mbs below 256 will not work.  Use the alternate CD.

FOr the XP problem, I got a with it, and I fixed it by reinstalling it.

---

### Post by Atomfix on 2007-08-18
lol, bah im not gonna bother now then lol, il stick with Win XP

---

### Post by overdrank on 2007-08-18
> **Atomfix said:**
> lol, bah im not gonna bother now then lol, il stick with Win XP

Hey there is alway xubuntu 
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)

---

