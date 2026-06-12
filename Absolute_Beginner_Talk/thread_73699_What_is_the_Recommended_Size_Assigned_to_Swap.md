---
title: "What is the Recommended Size Assigned to Swap?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by Anchovie on 2005-10-09
I have a Dell Inspiron 600m, 1.3GHz Intel Pentium Centrino w/ 1024KB Lvl 2 Cache, 512MB RAM @ 266MHz, and 40GB HD @ 5400RPM. What's the recommended HD space assigned to swap during the installation process?

---

### Post by aysiu on 2005-10-09
I'd do 512 MB. That should be more than enough. Unfortunately, if I'm remembering correctly, Ubuntu actually requires you to have a swap partition. With 512 MB of RAM, you probably won't ever use it.

---

### Post by matthew on 2005-10-09
[quote=aysiu]I'd do 512 MB. That should be more than enough. Unfortunately, if I'm remembering correctly, Ubuntu actually requires you to have a swap partition. With 512 MB of RAM, you probably won't ever use it.[/quote]
I once installed hoary with no swap whatsoever, so it is possible.

---

### Post by skoal on 2005-10-09
I agree with _both_ aysiu and matthew.  In your case, I'd go with 512MB max.  Whatever you do, throw it at the very end of all your partitions.  That way you can delete it, use it for another partition (if not needed), or just plain easily resize it.

By the way, I have yet to see my stupid swap even get touched during normal everyday desktop use.  Firing up Doom3 on the other hand, just a tad (~1% I believe).  I got ~792MB mem and a 256MB swap, btw.

\\//_

---

### Post by zerhacke on 2005-10-09
Wow, my swap is way off then.  I have 512Mb RAM, and always thought swap was supposed to be 2XRAM.  My 1024Mb swap is way too much then.

No wonder it's never used.  I have a lot of RAM for a Linux system and never do much besides compile, edit, surf, email, and instant message.  Of those I rarely do more than two at once.

---

### Post by darkmatter on 2005-10-09
[QUOTE=Anchovie]I have a Dell Inspiron 600m, 1.3GHz Intel Pentium Centrino w/ 1024KB Lvl 2 Cache, 512MB RAM @ 266MHz, and 40GB HD @ 5400RPM. What's the recommended HD space assigned to swap during the installation process?[/QUOTE]

The recommended size for swap in any Linux system is twice your RAM.

In your case 512MBx2=1024MB or 1GB.

Though you will most likely never need it, it is recommended to have a swap, and set it up in the above manner.

It's only precautionary.

---

### Post by void_false on 2005-10-10
[QUOTE=darkmatter]The recommended size for swap in any Linux system is twice your RAM.

In your case 512MBx2=1024MB or 1GB.

Though you will most likely never need it, it is recommended to have a swap, and set it up in the above manner.

It's only precautionary.[/QUOTE]

That was true when normal PCs had 32mb installed maximum. 512 should satisfy all your needs.

---

### Post by matthew on 2005-10-10
[quote=void_false]That was true when normal PCs had 32mb installed maximum. 512 should satisfy all your needs.[/quote]
Unless you have a laptop and want to suspend to disk. Then you need a swap at least as big as your ram.

---

### Post by ngms27 on 2005-10-10
If you don't have a swap then its probable your machine will go into a disk thrashing frenzy.

Ubuntu will use a swap even if you have sufficient memory as apps that haven't been serviced for a while are automatically put out to swap to allow better responsiveness for new apps being launched etc.

JonnyT

---

### Post by Goober on 2005-10-10
Erm, that reminds of a very n00bish question I have . . . what is a "Swap".  I know it's got something to do with a partition for your memory, it makes things faster or something, but . . . well, I don't ever remember making it, unless the Ubuntu install automatically does it.  If I don't have it, should I make one?  

And I do have 1.3 Gb of RAM, so I might not need one . . .

---

### Post by matthew on 2005-10-10
[quote=Goober]Erm, that reminds of a very n00bish question I have . . . what is a "Swap". I know it's got something to do with a partition for your memory, it makes things faster or something, but . . . well, I don't ever remember making it, unless the Ubuntu install automatically does it. If I don't have it, should I make one? 

And I do have 1.3 Gb of RAM, so I might not need one . . .[/quote] A swap partition is a place on your hard drive reserved to use as if it were more ram memory. With 1.3 Gb of ram you really don't NEED one. It still isn't a bad idea to have one, though. With the size of hard drives now days the loss of 512 or 1024 Mb isn't a big deal, even if the swap is only used once in a blue moon.

> If you don't have a swap then its probable your machine will go into a disk thrashing frenzy. Sorry, that's just not true. I have run without a swap in the past on a maching with 1 Gb ram and never missed it. I ended up creating a swap file because this was on my laptop and I wanted to be able to suspend to disk.

Unless your machine has 256Mb of ram or less you don't really NEED a swap, bt I still say it's a good idea to have one that is about 1.5x the size of your ram up to 1Gb or the size of your ram.

---

### Post by John.Michael.Kane on 2005-10-10
i have 512mem of which 277mb is being used i have 1gig of swap of which 182.5mb is being used. i guess the bottom line is it depends on what the machine will be used for.

---

### Post by blastus on 2005-10-10
I have 1024Mb of RAM and a 2048Mb swap. I've never seen the swap being used that much. 

There is a kernel option called "swapiness" or something like that determines the kernel's preference for using the swap. I'm going to eventually upgrade to 2048Mb of RAM so with that much RAM I think a 512Mb swap would be more than enough.

---

### Post by Goober on 2005-10-10
Hrm, so, if I wanted to create a swap partition, then how would I go about it?

Would I have to reinstall Breezy?  Also, since I have both Hoary and Breezy on separate partitions on the same HD, then could I just make one swap partition for them both?

---

### Post by matthew on 2005-10-10
To create a swap partition you first need to use fdisk, parted, gparted or something like that to make the partition and format it as "swap".

Then, once the partition is made you need to put it in your /etc/fstab like this, changing hda6 with whatever your partition number is:
```
 /dev/hda6       none            swap    sw              0       0
``` Then type
```
sudo mkswap /dev/hda6
``` to create the actual swap file on this partition and
```
sudo swapon -a
``` to turn it on.

The hardest part is creating the swap partition in the first place. The hard drive you are making it on cannot be mounted at the time you are partitioning and you will want to be sure you have backed up any data on it before you start messing with the partitions. You may not lose anything when you resize an ext3 partition, but you might lose it all so BACK UP first. Then boot to a live cd, Ubuntu, Knoppix, or another one that has an fdisk, parted, gparted, or other partitioning utility that you know how to use.

Hope that helps!

---

### Post by az on 2005-10-10
If you use guided partitioning when you install (default), then you do not need to worry about a swap.  It calculates the size and makes it for you.

The size of swap is the stuff religiour ways are made of.  It can be anything from 1 to two times your ram.  It depends.  You need a swap which is 25 per cent bigger than your ram to be able to go into hibernation (suspend-to-disk)

---

### Post by matthew on 2005-10-10
[quote=azz]The size of swap is the stuff religiour ways are made of. It can be anything from 1 to two times your ram. It depends. You need a swap which is 25 per cent bigger than your ram to be able to go into hibernation (suspend-to-disk)[/quote]
I didn't know that! Maybe that is why I have continued to have hibernation issues...need a free afternoon to play around a bit. Maybe when I do the Breezy upgrade I'll repartition as well.

---

