---
title: "[SOLVED] Did I screw up my install?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by eweibust on 2007-11-14
Last week I upgraded from 7.04 to 7.10 and I'm afraid I broke/damaged my install.  My machine has been slowing, then freezing.  I know this because with the new video options my windows go gray while they are hung, possibly waiting on resources.  I'm beginning to think I messed-up my swap space, possibly removing it all-together.

Here is what I see when doing a top:
top - 16:48:20 up  3:08,  3 users,  load average: 0.24, 0.44, 0.69
Tasks: 131 total,   2 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.6%us,  2.6%sy,  2.8%ni, 82.9%id,  1.8%wa,  0.3%hi,  0.1%si,  0.0%st
Mem:   1025920k total,  1005672k used,    20248k free,    27768k buffers
Swap:        0k total,        0k used,        0k free,   406416k cached

Shouldn't I have some numbers in the swap row?  The machine I'm running has 1 Gb of ram and 160 Gb hd.

Thanks...
Erik

---

### Post by Dr Small on 2007-11-14
You could try reinstalling with 7.10, as a fresh install and see if that helps :\

---

### Post by Scheater5 on 2007-11-14
With a gig of Ram, you probably aren't going to use Swap much unless you're doing some really process intensive work like rendering 3D graphics.  But why don't you try turning off the new visual effects.  It's built in Compiz-Fusion, a composite Window Manager that is pretty hard on weak graphics cards and can slow a computer to a crawl if it is not suited for it.

---

### Post by Yoooder on 2007-11-14
> **eweibust said:**
> Here is what I see when doing a top:
top - 16:48:20 up  3:08,  3 users,  load average: 0.24, 0.44, 0.69
Tasks: 131 total,   2 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.6%us,  2.6%sy,  2.8%ni, 82.9%id,  1.8%wa,  0.3%hi,  0.1%si,  0.0%st
Mem:   1025920k total,  1005672k used,    20248k free,    27768k buffers
Swap:        0k total,        0k used,        0k free,   406416k cached


Let's break it down a bit:

~10% CPU Usage -- this is a pretty normal number for a system at an idle state

~98% Memory Usage -- this is somewhat startling, as 1gb of RAM should be enough for most functions short of heavy database work or running Virtual Machines.  What all was running when you ran "top"?

If you're running out of memory then your machine would certainly slow to a crawl--especially when...

0k / 0k Swap in use -- your system doesn't have any swap!  Swap is essentially an overflow for memory, it's basically hard-drive based memory.  When your memory is full (as yours is) and it needs more then the swap partition acts as that fallback, however the swap partition is extremely slow compared to regular RAM--which is why it's just a failover.  However, any swap will help because without it your machine is hitting the ceiling.


So:  We've got 2 problems here, 1 is that your machine is burning through more memory than it should; and 2 is that your swap partition has either disappeared or isn't active.

Problem 1) We'll need more info to help, try running top and then pressing 'm' which *i think* should cause it to sort the process list in order of memory usage.  This should show you where all that memory is going, and give you some good problem candidates.

Problem 2) First we need to know that your swap partition still exists.  To check this run:
> sudo cfdisk /dev/[sda|hda|etc...]  <-- * just plug in your drive's name

In a default Ubuntu installation you'll see 2 partitions, the first will be "Linux ext3" or possibly "XFS" or "ReiserFS" or something to that effect, it's your main installation partition that holds your filesystem.  The second should be "Linux swap / Solaris" (or maybe just Linux Swap).  This is obviously your swap partition, if present.

If a swap partition is present then take note of its name in the left-hand column.  Mine is usually "hda5", but that can vary.  Also take note of it's size, which should be either 2 or 3 times the amount of RAM installed--so in your case expect somewhere around 2-3GB.

If you didn't find your swap partiton:
 - Then if there is open space on the drive (which would show in cfdisk) you can re-create it.
 - If there isn't open space (your main partition is taking up 100%of the drive) you can research shrinking that partiton to make space for it, or reinstall Ubuntu.

If you found your swap partition:
 - Try running:
> sudo swapon /dev/[your swap name here]
which will enable and register your swap partition for the current session (until you reboot).  Try running "top" after this to see that it shows swap as available.  If it works then you'll need to add (or possible edit) a line for it in your "/etc/fstab" file, which tells Linux what partitions to mount and where.

A typical swap fstab entry will look like:
> /dev/[your swap name here]       none            swap    sw              0       0

---

### Post by Inxsible on 2007-11-14
your swap is probably not enabled since it shows 0K total. Try to enable using the swapon command the above poster gave and make sure you have the corresponding entry in fstab

---

### Post by flickerfly on 2007-11-15
> **Yoooder said:**
> Let's break it down a bit:

~10% CPU Usage -- this is a pretty normal number for a system at an idle state

~98% Memory Usage -- this is somewhat startling, as 1gb of RAM should be enough for most functions short of heavy database work or running Virtual Machines.  What all was running when you ran "top"?

If you're running out of memory then your machine would certainly slow to a crawl--especially when...

This is misinformation. Any linux system working properly should be taking up the majority of the RAM available to it. See this link for the rational behind this.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management)

Also, the load averages are "load average: 0.24, 0.44, 0.69". I don't think you can call that idle. It isn't busy to the point where you should see a significant performance cut, but it isn't idle. If I see numbers over 3, I'd get concerned. I've seen them as high as 19 and blogged about it. :-) [http://josiah.ritchietribe.net/blog/archive/2005/04/974/](http://josiah.ritchietribe.net/blog/archive/2005/04/974/)

---

### Post by eweibust on 2007-11-15
The problem appears to be a bug with the Ubuntu upgrade/update process.  My swap space was broken/disabled.

With some help I figured out the problem while looking at /etc/fstab.
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=572d6e46-8534-4094-b2a2-60b33b668031 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c1adac93-3270-456a-885e-be98f9fb25bd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

If you look at the line for /dev/sda5 that was the problem.  Appartently, the ugrade chances the way swap is listed in /etc/fstab and this was the issue.  I commented out the above line for /dev/sda5 and added the following.

/dev/sda5   none   swap   sw   0   0

then I did a mkswap and then a swapon.  After that a reboot fixed the issue.

Thanks to everyone for the help.

---

### Post by Inxsible on 2007-11-15
yes, swap should never be mounted.

Glad to know its working for you now. Mark the thread as solved please :D

---

### Post by Yoooder on 2007-11-15
> **flickerfly said:**
> This is misinformation. Any linux system working properly should be taking up the majority of the RAM available to it. See this link for the rational behind this.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management)

Also, the load averages are "load average: 0.24, 0.44, 0.69". I don't think you can call that idle. It isn't busy to the point where you should see a significant performance cut, but it isn't idle. If I see numbers over 3, I'd get concerned. I've seen them as high as 19 and blogged about it. :-) [http://josiah.ritchietribe.net/blog/archive/2005/04/974/](http://josiah.ritchietribe.net/blog/archive/2005/04/974/)

Interesting read, thanks for the info!

---

