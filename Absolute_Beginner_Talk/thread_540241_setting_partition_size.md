---
title: "setting partition size"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-09-01
ive setup ubuntu and edubuntu on this computer. with a swap shared between the 2 of them. I need to resize ubuntu, everything i try to add says its to big. this is a 300 gig HD and ive used about 50 gigs of space, the rest shows as unusable. how do i fix this without reformatting

---

### Post by louieb on 2007-09-01
If you  have GParted installed  please post a  screen shot. Its on the live CD too. under system>adminstration. Anyway heres a couple of links. I use the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") for most of my partition work.   [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by trucker33377 on 2007-09-01
[ATTACH]42270[/ATTACH]

i think i got this screen shot

---

### Post by louieb on 2007-09-01
The disk space is unusable now because you a limited to 4 primary/extended partitions.   You have a bunch  of options. 

The easiest thing to do is resize hda4 to take up the unallocated space and use it as you data partition. I noticed hda4 is not locked so its not mounted. You will have to mount it after resizing it. Or is hda4 you  edubuntu install? 

The other not much harder but you will need the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") or [SystemRescueCd]("http://www.sysresccd.org/Main_Page"). I prefer the second nice tool to have around. 

You could move hda3 and hda4 somewhere in the middle of the unallocated space. and expand both hda2 and hda4.

When GParted start moving the partitions around it is going to take some time I will guess from experience 2 hours or more. So don't worry if it takes a while. 

After you a finished. You probably will find that swap does not work and you may have trouble boot the distro in hda4. Not a problem it means the uuid of the partitions has changed. 

You will have to go into /boot/grub/menu.lst and /etc/fstab and fix the uuid. To find what uuid to use at the terminal
```
ls -l /dev/disk/by-uuid/
```You have a lot of ways you can go. Might just look at the wikipedia entry about partitions.  Good luck and back your important stuff up first.

BTW there is a way to have more that 4 partitions. And if you are prepared  to wipe your disk. I will go into that later.

---

### Post by trucker33377 on 2007-09-01
well the main reason i dont want to wipe this is i just got my wireless nic to work on here and im not sure how i did that the 256 windows partition is not really needed i dont think.

 all i have on here that i use is linux , i could remove edubuntu and reinstall that if thats an option or remove windows if you dont know any reason i should keep it on here

---

### Post by trucker33377 on 2007-09-03
[ATTACH]42461[/ATTACH]

got it done i have gparted and a disk and was able to resize and move what i wanted. and it didnt miss with grub at all logged right on no prob thanks for the help

---

