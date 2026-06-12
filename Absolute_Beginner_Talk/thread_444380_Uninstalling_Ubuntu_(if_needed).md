---
title: "Uninstalling Ubuntu (if needed)"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-15
Hi,

I recently dual booted Edgy on my pc and I love it and I'm thinking about putting it on my parent's computer as well (I've already got plans to put Xubuntu on a much older pc of theirs that we ignorantly installed XP on, that thing's become completely unuseable afterwards.  It only had a 6 Gb hard drive, 64 Mb Ram and was less than 1Ghz, I forgot what exactly it was...it's an old computer).

While I'm pretty sure they'll like it there's still the chance that I'm wrong and before I mess around with their PC I want to make sure that I'll be able to uninstall Ubuntu if need be.  Could someone tell me how to go about doing that?

---

### Post by Zzl1xndd on 2007-05-15
the easy ansure is wipe the Ubuntu partitions and use the windows disk to re-write the MBR. Oh and reformat the Ubuntu partitions in a windows friendly format.

---

### Post by mahy on 2007-05-15
AFAIK, no operating system provides a way to uninstall itself. You have to use some external environment. In case of a REAL need, look here: [http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

---

### Post by zhinker on 2007-05-15
Could you be a bit more detailed about that?  I'm not really experience in partitioning the hard disk, I used the software on the Ubuntu CD when I was installing it on my computer and don't know what to use when I try deleting the Ubuntu partitions, and how to I reformat the Ubuntu partitions after that?

and here's a separate question:  based on the specs I listed above for the older computer I'm planning on putting Xbuntu on (6 Gb hard drive, 64 Mb Ram, and speed<= 512Ghz) will I be able to run beryl on it decently?

---

### Post by earobinson on 2007-05-15
Just re install windows or remove the ubuntu partition using the ubuntu live cd.

---

### Post by Zzl1xndd on 2007-05-15
> **earobinson said:**
> Just re install windows or remove the ubuntu partition using the ubuntu live cd.

Yep if you install Ubuntu without a Dual boot then just reinstall windows if its a dual boot use the Ubuntu Cd to remove them, or if you have something like Partition magic for windows you can use that to change the partitions as well.

---

### Post by lazyart on 2007-05-15
> **zhinker said:**
> and here's a separate question:  based on the specs I listed above for the older computer I'm planning on putting Xbuntu on (6 Gb hard drive, 64 Mb Ram, and speed<= 512Ghz) will I be able to run beryl on it decently?

Don't try beryl on that box.  Xubuntu is a good choice but leave it at that.  It'll be an email/web surfing machine I presume?

---

### Post by lazyart on 2007-05-15
..and I believe you need 256 mb ram to run the live CD..

---

### Post by jfinkels on 2007-05-15
> **lazyart said:**
> Don't try beryl on that box.  Xubuntu is a good choice but leave it at that.  It'll be an email/web surfing machine I presume?

Xubuntu may even be too heavy for the amount of RAM you have. If I were you, I would give Fluxbox a try (it's another desktop environment, like GNOME, KDE, XFCE, etc.): [http://fluxbuntu.org/](http://fluxbuntu.org/)

And' I'm going to go out on a limb and say it will be very difficult if not impossible to get Beryl/Compiz to work with that system.

---

### Post by zhinker on 2007-05-15
> **lazyart said:**
> ..and I believe you need 256 mb ram to run the live CD..
The xubuntu website said it only needed 64 Mb to run and be installed with the alternate CD (I'm not even sure if the memory on that machine is 64 or 128Mb) so that shouldn't be a problem, and yeah it'll be mainly just for internet stuff and OpenOffice type programs.  I'm assuming (hoping) it should be able to play Flash games just fine like those on Nick.com, because my plan is to make it the 'kiddie' computer, letting the grown ups work on their stuff on the other PC.

So if I were to use the Ubuntu CD to repartition the drives to delete the Ubuntu partitions, how would I do it?  I'm assuming I would start off the same way I would if I was installing Ubuntu, and when I get to the partition manager I'd simply delete the Ubuntu partitions and expand the XP one, but where does it go from there?  Because it seems to me like the CD would either give me an error or try to install Ubuntu onto non-existant partitions.

---

### Post by jfinkels on 2007-05-15
> **zhinker said:**
> The xubuntu website said it only needed 64 Mb to run and be installed with the alternate CD (I'm not even sure if the memory on that machine is 64 or 128Mb) so that shouldn't be a problem, and yeah it'll be mainly just for internet stuff and OpenOffice type programs.  I'm assuming (hoping) it should be able to play Flash games just fine like those on Nick.com, because my plan is to make it the 'kiddie' computer, letting the grown ups work on their stuff on the other PC.

So if I were to use the Ubuntu CD to repartition the drives to delete the Ubuntu partitions, how would I do it?  I'm assuming I would start off the same way I would if I was installing Ubuntu, and when I get to the partition manager I'd simply delete the Ubuntu partitions and expand the XP one, but where does it go from there?  Because it seems to me like the CD would either give me an error or try to install Ubuntu onto non-existant partitions.

If you want to delete the Ubuntu partition and resize your Windows partition to fill the whole drive (or whatever size you want), boot into the Live CD environment, open the program "GParted" and you will be able to delete, create, resize, format, etc. whatever partitions you want. Or you can download the Gparted Live CD from their website, which provides a simple environment for you to edit partitions.

---

### Post by zhinker on 2007-05-15
Thanks, I'll try that

---

