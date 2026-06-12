---
title: "I need so much help...."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Fowlwing on 2007-03-30
Hi im new to ubuntu, and.... i really dont understand it... so its driving me to be fustrated.... and its driving me to not likeing it.    Is there some way i can.... make my computer "Go Back" to an earlier date before i installed ubuntu?

---

### Post by Parasitesss on 2007-03-30
Youre going to have to ask someone familiar with windows, which are most of the people in this forum.

---

### Post by martinw89 on 2007-03-30
Well, it depends.  Did you install Ubuntu on a separate partition than Windows?  Did you completely overwrite windows?  Do you have any backups?  Because Ubuntu is not just any old software, but an OS, it's very hard to just "go back" unless you backed up.

---

### Post by cowlip on 2007-03-30
put in your windows disk, choose "recovery console", and type "fixmbr" or "fdisk /mbr"

That's if you have Windows and ubuntu installed, not only ubuntu installed.

Maybe you can use [Wubi ]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html")next time if you ever want to try Ubuntu again, it doesn't partition or anything, it just installs as a file on your windows partition.

---

### Post by L337reap0r on 2007-03-30
Well, if you are still running off the live CD, and haven't actually installed Ubuntu, then reverting to whatever you have before is as simple as rebooting and taking out the CD. If you have installed it, however, and you only had one partition (the most likely scenario) then you would need to reinstall your old OS, or run any system restore disk that may have come with your computer. If you had multiple partitions, and installed Ubuntu separate from your old OS, then Ubuntu's bootloader should give you the option to load the other one.

However, If you would like help with using Ubuntu, or if you have any questions on it, feel free to ask away here. Most of the people are very friendly. :)

---

### Post by Fowlwing on 2007-03-30
uhhh... i dunno if i installed ubuntu over windows.....  how could i find this out?

---

### Post by L337reap0r on 2007-03-30
Have you run the "Install Ubuntu" link on the desktop since putting the CD in?

---

### Post by martinw89 on 2007-03-31
If you did install Ubuntu type ```
sudo fdisk -l
``` in a console (Applications-> Accessories-> Terminal).  This will list your partitions.  For example, mine looks like this:```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7406    59488663+   7  HPFS/NTFS
/dev/sda2            7407        9630    17864280   83  Linux
/dev/sda3            9631        9729      795217+   5  Extended
/dev/sda5            9631        9729      795186   82  Linux swap / Solaris
```
See the /dev/sda1?  That's my first partition, and it's Windows (I can tell because the filesystem is NTFS).  Don't worry, plenty of people are happy to help you get back to a computer that works for you :)

---

### Post by GSF1200S on 2007-03-31
> **Fowlwing said:**
> uhhh... i dunno if i installed ubuntu over windows.....  how could i find this out?

ok, take the Ubuntu disc out of the CD drive and reboot. If you installed it as a multi-os platform like I did, then Grub will come up.

Grub is a program allowing you to select your OS. It will be a black screen with white writing on it. If its a dual boot system, it will have Ubuntu listed on top with a number next to it, and the word generic or recovery next to the number. Listed below the Ubuntu option, there should be a portion that says "Other operating systems." For example, the whole screen may look like this:

Ubuntu 2.6.20.13 Generic
Ubuntu 2.6.20.13 (recovery)

Other operating systems installed:
Windows XP Home Media Center Edition

Selecting Windows will boot windows (just being clear).

If this screen doesnt come up and it boots straight to Ubuntu, then I regret to say youve installed over your other OS (probably windows?). We can then give you advice on how to repartition and reinstall Windows, but all the files, folders etc will be gone. I would recommend a dual boot setup. Its easy, and if Linux gets a little overwhelming, then you can simply boot windows and relax. Linux is just different than what youre used to. I remember being a little frustrated and lost, but I searched these forums and the net, and now with little more than a weeks experience, I can move around Linux easily, and im quickly beginning to remember commands, locations, etc.

Im not trying to give a pep talk here.. I just want you to get your other OS back for a reprieve, and hopefully grant you a little patience to give this awesome OS a chance.

---

### Post by GSF1200S on 2007-03-31
> **martinw89 said:**
> If you did install Ubuntu type ```
sudo fdisk -l
``` in a console (Applications-> Accessories-> Terminal).  This will list your partitions.  For example, mine looks like this:```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7406    59488663+   7  HPFS/NTFS
/dev/sda2            7407        9630    17864280   83  Linux
/dev/sda3            9631        9729      795217+   5  Extended
/dev/sda5            9631        9729      795186   82  Linux swap / Solaris
```
See the /dev/sda1?  That's my first partition, and it's Windows (I can tell because the filesystem is NTFS).  Don't worry, plenty of people are happy to help you get back to a computer that works for you :)

Haha, I nuked matters a little.. This guy has a much easier method. Yeah, dont get frustrated.. I like having my Windows for gaming, and if thats what your comfortable with, than it needs to be there. Good luck...

---

### Post by Fowlwing on 2007-03-31
yeah... i installed over windows.... B(....  o well....see i dont have any windows os cd's i can use on this computer... cause i bought this one from a yardsale so i could have it in my room.... and my other computers are compaqs... so   i guess.... the disks dont work on mine seen as its a gateway....

---

### Post by martinw89 on 2007-03-31
Don't sweat it, you still have options.  The compaq CD will work, Windows is Windows.  At the worst you will have some links to Compaq technical service on your computer.  But, to use that disk you will need the key code for your current computer (that might be tough to get if you got it at a yardsale...)  If you just want XP you can get it for [pretty cheap]("http://www.newegg.com/Product/Product.aspx?Item=N82E16832116169").  Vista does not cost much more if that's what you're in to.

---

