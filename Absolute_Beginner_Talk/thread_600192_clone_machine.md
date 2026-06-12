---
title: "clone machine?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-11-02
Hi, 

I have an old bucket of bolts that I have managed to install a very nice headless Gutsy server on. The machine is LAMP based but has *lots* of nice extras... it is now *just right* for what I need. I have spent many many many hours researching settings for this machine and I have forgotten half of them.

I backup all *data* on the machine but I am worried that if the OS Disk crashes or the machine catches on fire that ill have weeks of re configuring to do.

Is there a disk imager for ubuntu? and if so, how successful would i be if I had to rebuild this image on another machine? would all the drivers just auto-magically sort themselves out?

is there some other solution to rapidly restore system services on a new box?

cheers

c.

---

### Post by shad0w_walker on 2007-11-02
You can literally stick the whole filesystem into a tar file and be able to backup that way. I assume seems as your running a headless setup you know what your doing to a reasonable extent.

[http://ubuntuforums.org/showthread.php?t=35087&highlight=ubuntu+back+up+howto](http://ubuntuforums.org/showthread.php?t=35087&highlight=ubuntu+back+up+howto)  

That link should help you out with the backup and restoring. There is also things like partimage but be aware that it wants a partition atleast as big as the original backed up partition, even if it was not full when backed up.

---

### Post by sloggerkhan on 2007-11-02
If you want to go hardcore with imaging, look up clonezilla.

---

### Post by gate on 2007-11-02
My preferred solution for this is taking a complete image of the hard drive. Utilities such as Clonezilla or Ghost for Unix (g4u) will backup the whole drive and make it so you can just dump the image back on when there is a problem. Of course just taring up and compressing / might get you what you need as well. Everything is stored in files on Linux.

 I have used Clonezilla for imaging a computer and spamming the image out to multiple identical computers, it worked fine when I did it one at a time.

---

### Post by cnschulz on 2007-11-02
know what im doing!? pfft.

a little knowledge is dangerous... but yes i have learnt *heaps* via this forum.

thanks once again. I will check out clonezilla... but its really the machine specific drivers (i assume there are many) that are copied at install time that i was worried about... or does it install *all* of them? the point is that this image will be on to a new (different) machine.



Im running a celeron with 400mb of memory with LAMP, Tomcat, MyTunesRss, samba, munin, awstats, torrentflux and a bunch of other utilities (and i rarely page to disk). 

Try doing that on windows! I heart ubuntu.

---

### Post by shad0w_walker on 2007-11-02
I believe and i stress the word believe (Not 100% sure but reasonably) that when stuck into a new system Ubuntu is able to get the drivers it needs automatically configured. If memory serves it loads up all the generic drivers and should be able to detect the change during boot up and work nicely anyway. 

Obviously drivers of things that are a pain in the *** will need to be manually setup if they are new (Mostly drivers for rare/beta supported stuff)

---

### Post by cnschulz on 2007-11-02
thank you all very much

:)

---

### Post by julian67 on 2007-11-02
Another vote for Clonezilla, or more exactly the [GParted-Clonezilla LiveCD]("http://gparted.sourceforge.net/livecd.php") 

> This is a multi-boot livecd booting off GRUB. It can load the last GParted-livecd or Clonezilla
to backup file system localy or through the network. Clonezilla supported ext2, ext3, reiserfs,
xfs, jfs of GNU/Linux, and FAT, NTFS file system.
UnlikePartimage or ntfsclone, which only for partitions. Clonezilla, containing some other programs,
can save and restore not only partitions, but also a whole disk.
Unlike G4U or G4L, in Clonezilla, if file system is supported, only used blocks in harddisk are
saved and restored. This increase the clone efficiency.
For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.

Clonezilla Live is much simpler than Clonezilla and perfectly suited to imaging/backing up a single machine or a single partition. 

[Linux.com:Manage partitions and disks with GParted-Clonezilla live CD]("http://www.linux.com/feature/115208")

> Backing up partitions and hard disks sounds like work -- until you've tried Clonezilla. With Clonezilla you can clone and duplicate partitions of various formats and disks of various sizes locally or over the network. Even more impressive is the fact that you can do all this without typing complicated commands. And since Clonezilla is available as part of the GParted-Clonezilla live CD, you don't even have to install it

---

### Post by Daveski on 2007-11-11
> **shad0w_walker said:**
> I believe and i stress the word believe (Not 100% sure but reasonably) that when stuck into a new system Ubuntu is able to get the drivers it needs automatically configured. If memory serves it loads up all the generic drivers and should be able to detect the change during boot up and work nicely anyway.

I can confirm that I have fully configured a fairly complex Xubuntu setup on an old Compaq Armada, and then put the the HD into an old IBM ThinkPad 390. The machine works perfectly, although I did have to delete the xorg.conf file as the display settings and resolution are different on these machines.

---

