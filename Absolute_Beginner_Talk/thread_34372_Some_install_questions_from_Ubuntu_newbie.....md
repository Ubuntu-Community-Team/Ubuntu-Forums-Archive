---
title: "Some install questions from Ubuntu newbie...."
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by Pattycake on 2005-05-14
This is my first foray into Linux although I am a past 'master' of Windoze and build my own rigs.  Not bad for a girl, right?  But this Ubuntu install is giving me the cold sweats.  

I just received the double CD pack and liked the Live version very much.  I'd wanted to install it to the slave on my WinXP system and got as far on the expert install as formatting and partitioning which I do NOT want to do.  It mentioned some type of Manager as a choice and said if I chose it no changes would be made to the existing partitions. Since I want to keep my XP and all my data, how should I proceed from here?  Will this Manager allow me to put Ubuntu on a drive of my choice and dual boot with XP, or is the dual boot controlled from XP?

This forum is very informative but so far I haven't found the answer.

Thanks

---

### Post by nad on 2005-05-14
The dual boot will necessarily be controlled by a program other than one by M$ as it is not possible to boot a non-M$ os from a M$ mbr (as far as I know).

My favorite method of partitioning is to do it first from an interface that I am familiar with and certainly not as unintuitive as the ubuntu partitioner. Use the live cd to do the partitioning. You have a choice of several command line tools and I believe that gparted or qtparted is there for a gui. This way you can use an interface that you are familiar with or at least can become acquainted with and research before you commit your changes.

---

### Post by az on 2005-05-14
By default, the installer will blow away the first hard drive it finds.

You just need to tell it to blow away the second hard drive (if that is the correct one)

After that, it will use guided partitioning to calculate the size of a swap partition to put on that drive.

The first ide device is called hda and the second hdb and so on.  If your cdrom is the second ide device, your second hard drive may be named hdc....

It is scary, but it is really simple and the installer's partitionner does a good job of being straightforward.  It is also rock solid.  You can be assured that many many people have used it to resize NTFS partitions without any problems.


Oh yeah, forget about the expert option.  That is there only for the situation where you have hardware that gives you problems and you want the installer to not try to load certain modules and the like.  Picking expert will not give you any more advantage in most cases.

---

### Post by soonindallas on 2005-05-14
I installed ubunto about an hour or so: dual boot with XP on this new laptop.  contrary to nad, no offense dude ;-) I did not find the partioning excercise unintuitive.  i guess the best solution would be to install on a different physical drive, but the grub dual boot utility works fine and both OS's work just fine.  go for it!

---

