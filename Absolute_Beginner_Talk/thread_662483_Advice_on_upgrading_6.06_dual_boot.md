---
title: "Advice on upgrading 6.06 dual boot"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by anothernewuser on 2008-01-09
I'm currently running a dual boot Windows XP / Ubuntu 6.06 and am considering upgrading both to Vista / 7.10.

First, does anyone have any advice on which operating system to upgrade first?

Second, I may hold off on Vista (my understanding is Vista may not recognize the existing Ubuntu anyway) and go with 7.10 first but I installed 6.06 a long time ago and successfully played around with the partitions in order to create a spot for Ubuntu to install,  I don't remember what I did though as it was a long time ago and I'm only an infrequent user.  Soooo .... I created a live disk of 7.10 to play around with and when I went through the install process to see what the steps were ... I got to the part where I have to specify partitions and wasn't sure what to do.  

My 2 options are "Guided" (which gets me to the end of the install process but has me a bit scared about allocating partitions) and "Manual" which wants me to specify a root and swap partition.  To be honest, the partitions are intimidating me at the moment and I'm gonna go slowly.  With the "guided" option at the end it tells me that it will use partition #1 for the root and partition #5 for the swap.  As 6.06 as already has a swap I assume 7.10 will use the same partition so that doesnt bother me ....   but is partition #1 likely to be where Windows XP is now or where 6.06 is?  Will it matter? What has me spooked is that 7.10 will install itself over XP.  I kind of hoped it would automatically put itself over 6.06 (and maybe it is?).


Anywho ... hope thats clear enough for someone to understand.

Any advice will be greatly appreciated ... I"m off to search through some other threads now to see if this has been asked (should have doe that first I suppose).

---

### Post by frup on 2008-01-09
If installing fresh, it is always easiest to install windows first. Personally I wouldn't touch vista at all... It's not really an upgrade.

With the install provided you pick the correct partition under guided (the one containing the 6.06 install) everything should go smoothly. Ubuntu should be on the second partition. The easiest way to check is to see the sizes of your C drive in windows and your / in Ubuntu and compare them to the partition size. typing fdisk -l in terminal will also give you the information and the ubuntu one will be ext3 and the XP one will be formated in NTFS. If you can bare to wait 4 months though you can upgrade from 6.06 to 8.04 over the internet, then you won't have to worry about installing again if you prefer that method. Wait a week or two after the release (maybe May) for faster servers and ironing out of any upgrade problems that could (but shouldn't) exist. 8.04 is the next LTS release and you may prefer that. Coming from 6.06 you will probably be amazed by the improvements made in 22 months.

---

### Post by zvacet on 2008-01-09
```
cat /etc/fstab
```

Post it here and we will see what are your partitions look like.

---

### Post by houstonbofh on 2008-01-09
Vista has many issues, and does not work and play well with other operating systems.  I am frequently downgrading factory Vista machines to XP for clients.  I am also converting several to Ubuntu, something I had a much harder time doing with XP.  Think long and hard about this.  If you really want it, the best way is to buy another hard drive, remove all others, install Vista on it, then make it the second hard drive and point gurb at it to boot Vista.

As to the 6.06, there is a lot of testing underway to make a clean upgrade directly from Daper to Hardy when it comes out.  This may be a better solution for you.

---

### Post by shareMenaPeace on 2008-01-09
I recommend to download linuxmint.com :D (daryna release).
And it make snot much diffrence if i install first ubuntu and than vista, even vista kept my grub boot loader.

Just in case if you mess up grub try this disc for grub it is super.[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


Cheers

---

### Post by anothernewuser on 2008-01-09
Before I forget ... thx for you answers. 

"I wouldn't touch vista at all... It's not really an upgrade" - I like that.  It hadn't occurred to me to wait for the next LTS.  That's certainly another option.  "fdisk -l" got me no output at all though.

Zvacet here's he output you asked for:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda3       /media/sda3     ext3    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by zvacet on 2008-01-09
It look that **/dev/sda2** is your root partition and you will install on top of it.But,waiting for 8.04 is not bad idea,because then you will be able to upgrade directly from one LTS to another.Your choice.

---

