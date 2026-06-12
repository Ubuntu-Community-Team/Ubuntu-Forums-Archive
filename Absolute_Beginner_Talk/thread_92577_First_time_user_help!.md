---
title: "First time user help!"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by diggs on 2005-11-19
Allright, so I have XP on the first partition, 15 gigs.
I made a 15 gig fat 32 for ubuntu.
30 gig fat 32
and the another 18 gig fat 32.
I did all this in XP using the disk manager.

pop in the ubuntu CD, it acts funny and does some funny stuff. disconect my video card. finally it starts up. but now when I donut have the CD in, it just keeps asking for it! it just hangs up, after the bios screen until I put the disk in.

Ideally I would like to have the option of starting XP or ubuntu.
But I have no idea how to do this, hell I'm not even sure if ubuntu is actually installed! I think it is just running off of the disk. now what? Thanks for your help!

---

### Post by aysiu on 2005-11-19
Ubuntu (and any other Linux distro) will not work on a FAT32 filesystem. You need a Linux native one like Ext3 or Reiserfs. Fortunately, once you've made your FAT32 partition, you can reformat it as Ext3 during the installation process.

[This tutorial](http://users.bigpond.net.au/hermanzone/) has everything you need to know about dual booting.

---

### Post by diggs on 2005-11-19
[QUOTE=aysiu]Ubuntu (and any other Linux distro) will not work on a FAT32 filesystem. You need a Linux native one like Ext3 or Reiserfs. Fortunately, once you've made your FAT32 partition, you can reformat it as Ext3 during the installation process.

[This tutorial](http://users.bigpond.net.au/hermanzone/) has everything you need to know about dual booting.[/QUOTE]
Thanks! that tutorial was helpful.

I figured out what the problem was, my HD just died. :o  didn't see that coming. at least there was nothing of value on it, just the XP OS...

---

