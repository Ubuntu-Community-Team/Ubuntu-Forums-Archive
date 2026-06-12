---
title: "WindowsXP won't install"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-10
I love Ubuntu and I love video games, so I decided to reconfigure the partitions on my hard drive so that i have maximum space to work on ubuntu and enough space to play any game i desire on windows.

The only problem is, now that i've got partitions configured the way i want (Gparted), windows will not install.

I've tried 2 configurations

```

config 1:

sda1 - small 40 meg dell service partition (cannot change location, cannot change size)

sda2 - nfts partition alloted for windows (30gigs)

sda3 - ubuntu partition 110 gigs

sda4 - swap

```

```

config 2:

sda1 - small 40 meg dell service partition (cannot change location, cannot change size)

free space - 30 gigs (alloted for windows)

sda3 - ubuntu partition 110 gigs

sda4 - swap

```


What happens is that when i run the windows cd, it starts off detecting my devices and starting windows, however, as soon as it gets past the "starting windows" stage, it crashes, telling me that something is wrong and that windows must be shut down.

what's going on here and how can I install windows? (I am aware that grub will go away, i plan to reinstall that)

---

### Post by raja on 2007-06-10
Was this after a fresh install of windows into the partition or after shrinking the partition in which windows was already installed.
Because if it was the latter, there is atleast the possibility that the NTFS shrinking damages some files.

---

### Post by Tyke91 on 2007-06-10
this is an attempt at a fresh install of windows.

---

### Post by Shazaam on 2007-06-10
What I have found that works for me is to wipe the drive clean, install Windows, boot to safe mode and do a defrag. Then I use gparted to shrink Windows to a manageable size, add an extended partition using the free space, and partition the free space for Linux. I once had 7 flavors of linux inside the extended partition and they ALL worked. Here is an interesting link about dual-booting... 

[http://www.shell-shocked.org/article.php?id=230](http://www.shell-shocked.org/article.php?id=230)

---

### Post by Tyke91 on 2007-06-10
lol... i want to save my linux data

and i cant wipe the drive clean... that dell service partition wont go away.

---

### Post by KingJohn on 2007-06-10
Of course you can wipe the drive clean.  Fdisk and gparted respect nothing.

That doesn't mean it's a *good idea* to wipe the drive clean, though.

I'd start, at this point, by backing up your ubuntu data to another disk, and using Dell's built-in restore functions to return your machine to factory settings.

From there, use gparted to shrink the Windows partition to 30GB, and then use a Ubuntu liveCD to install in the last partition.  Finally, restore your ubuntu data from the backup.

---

### Post by Tyke91 on 2007-06-10
hmm... i'd rather not go out and buy another disk tho... is there no way i can just install windows on that 30 gb?

---

### Post by KingJohn on 2007-06-10
Well, my normal suggestion would have been to just let the Windows installer disk handle things.  After all, booting into the Windows CD SHOULD give you the option to choose a partition and install, but it's failing for you.

And if that's failing, there's not much I can really suggest to you that isn't scorched earth.  Sorry.

---

### Post by Tyke91 on 2007-06-10
thx for the help... i've checked my house and there is an old computer in my attic with a large enough hard drive... ill just cannibalize it from that and make a backup.

---

### Post by iroko on 2007-06-10
All documentation and tutorials I've read about dual booting with Windows XP say XP **must** be installed first.

---

### Post by KingJohn on 2007-06-10
Since Windows wipes out your boot loader when it installs, that's fairly close to true.  It doesn't *have* to be installed first, but you need to know how to re-install grub and set up multiple boots, meaning that in practice it's simplest and much easier to install Windows first.

---

### Post by eddieb on 2007-06-10
Please note. On any machine with Windows on it, Windows MUST be on the FIRST partition of the FIRST hard drive. NO BUTs!

---

### Post by Tyke91 on 2007-06-10
lol... windows was the second partition on my machine....

---

### Post by shae on 2007-06-10
I do not think that this is caused by the hard drive setup.  I actually think the problem is with the windows install disk.  I have experienced similar problems before, I think.  Are you using a  backup or custom-made copy of the XP disk?  Sometimes I would have this problem with some of the disks I slip-stream drivers into because of burning errors.  

Are these the disks the computer originally came with?  Sometimes dell puts special drivers on their install disk to make it run.  If it is a SP1 disk, you might ought to try slipstreaming SP2.

I hope this helps.

---

### Post by KingJohn on 2007-06-10
> **eddieb said:**
> Please note. On any machine with Windows on it, Windows MUST be on the FIRST partition of the FIRST hard drive. NO BUTs!

I know that's not exactly true- Toshiba ships their laptops with Windows XP on the second partition of the HDD, with an unmounted "invisible" first partition at the front of the drive that's only supposed to be accessible when you're restoring to factory default.  

I've never tried to set one of those to dual-boot, though, so I'm not sure how much trouble you'd have.  As I said, my personal solution would be restoring to factory settings with Dell's restore disk, then installing Ubuntu again from scratch once you've got Windows working, because while it might not be the most efficient or elegant way of doing things, it's certainly the simplest - and I'm much happier to let my computer waste it's time than to waste my own.

---

