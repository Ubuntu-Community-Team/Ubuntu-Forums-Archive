---
title: "Partition Help"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by bobx232 on 2007-07-29
I'm a complete newb when it comes to partitioning and such, so I would like some help.

I am trying to set up a dual-boot with Ubuntu and XP.  I'm using a Live CD, and I have gotten to the partition part.  When I use the first option, an error comes up, saying "partition resizing failure", or something along those lines.  So then it takes me to the (I think) manual way of setting up a partition.

And that's when I get stuck.  How do I manually set up a partition for Ubuntu, while keeping my XP data safe?

BTW, I'm using the How to Dual Boot Ubuntu and XP Guide from help.ubuntu.com, but I have no clue what it is saying in the partioning part

---

### Post by bobx232 on 2007-07-29
...Anybody?

---

### Post by logos34 on 2007-07-29
did you defrag windows first?

---

### Post by asmoore82 on 2007-07-29
If Winders's partition already occupies the entire disk and it can't be resized you may not be able to install Ubuntu without re-installing Winders with a smaller partition.

---

### Post by bobx232 on 2007-07-29
I analyzed C: using the built-in defragmenter windows has, and it told me that It was fine and I didn't need to defrag it.

---

### Post by expatCM on 2007-07-29
A work around may be to resize / define your partitions from XP using a product such as Partition Magic or say Partition Logic. ([http://partitionlogic.org.uk/](http://partitionlogic.org.uk/))

The only way to keep your XP data safe is to back it up to some form of media which may be physically removed from your computer.  Oh, and do check that the backup is good (that it can be read) since errors have been known to occur.

---

### Post by alienexplorers on 2007-07-29
Your best bet would be to save all data you need on a cd or dvd from your XP Data.  Then I would do a clean rebuild of the system.  I would make windows partition smaller while leaving say 20GB for Ubuntu and an extra 512MB swap.  Any other data can be placed in a Fat32 partition so it is available to both Ubuntu and XP.

---

### Post by bobx232 on 2007-07-29
Here's what my list of partitions say...

Device: /dev/sda
Everything else is blank


Device:/dev/sda1
Type:ntfs
Mount point:/media/sda1
Size:190546 MB
Used:26500 MB

Device:free space
Size:8 MB

Device:/dev/sda2
Type:fat32
Mount Point:/media/sda2
Size:9491 MB
Used: unknown

---

### Post by logos34 on 2007-07-29
> **bobx232 said:**
> I analyzed C: using the built-in defragmenter windows has, and it told me that It was fine and I didn't need to defrag it.

Possibilities:

--the windows partition is trying to automatically mount during resizing, thus causing the installer to error out
--there are 'unmovable' files at the end of the windows partition.  Go into windows and temporarily disable hibernation (power options) and virtual memory/paging file (system>advanced).  See if that helps.

You could also try using gparted gui on the ubuntu live cd to do the resizing first (system>admin>gnome partition manager)

---

### Post by bobx232 on 2007-07-29
What filesystem should I choose for my new partition?

---

### Post by bobx232 on 2007-07-29
And what's a swap partition?:confused:

---

### Post by alienexplorers on 2007-07-29
Its a partition in Ubuntu that lets you swap out data to your disk if you run out of main memory space.

---

### Post by bobx232 on 2007-07-29
Oh, ok, thank you.

And could you answer my other question for me?  I'm using GParted to make a new partition, except I don't know what filesystem I should make it.  Does it matter?

---

### Post by bobx232 on 2007-07-29
...Can anyone tell me?

---

### Post by bobx232 on 2007-07-29
Does it even matter?

---

### Post by alienexplorers on 2007-07-29
A swapfile is a generic file partition unlike / & /home which should hopefully be ext3.  As far as I know I never selected a partition for swap other than /swap.

---

### Post by SentientFluid on 2007-07-29
> **logos34 said:**
> Possibilities:

--there are 'unmovable' files at the end of the windows partition.  Go into windows and temporarily disable hibernation (power options) and virtual memory/paging file (system>advanced).

The hiberfil.sys and pagefile.sys are only unmovable when in use.  If he's properly booted to a Live CD then those files are not in use and would be treated just like any other data files.  Essentially, when booted to the Live CD all files/folders on the Windows partition should be unlocked and mounted read & write.

[QUOTE=bobx232]And could you answer my other question for me? I'm using GParted to make a new partition, except I don't know what filesystem I should make it.[/QUOTE]

Use ext3 for any Ubuntu partition (except the swap partition).  If you need to access any information on an ext3 formatted drive when you're booted to Windows, then you may want to install [Ext2 IFS For Windows]("http://www.fs-driver.org/").  I use it to read my ext3 drives and it works fine.

---

### Post by logos34 on 2007-07-30
> The hiberfil.sys and pagefile.sys are only unmovable when in use. If he's properly booted to a Live CD then those files are not in use and would be treated just like any other data files. Essentially, when booted to the Live CD all files/folders on the Windows partition should be unlocked and mounted read & write.


Well all I can say is that procedure has worked for countless others having problems during install.  
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

NTFS does NOT mount as read+WRITE on live cd--you need the ntfs-3g driver for write support!

---

### Post by SentientFluid on 2007-07-30
> **logos34 said:**
> NTFS does NOT mount as read+WRITE on live cd--you need the ntfs-3g driver for write support!

Thanks for pointing that out. I´ve had NTFS write support enabled for so long I had almost forgotten that. :)

---

