---
title: "[SOLVED] Ubuntu continually crashing, even during install"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-16
With what began as a [problem ]("http://ubuntuforums.org/showthread.php?t=668970")during my blank-screensaver, it's quickly matured into a complete in ability to do anything.

However since I've been in the room one thing that I've noticed that *seems* to proceed each screen freeze is the "clunking" sound of my hard drive powering down.  But I'm not sure if this is a cause or an effect of the lock up.  All this morning I've been booting off of the LiveCD and trying to reinstall Ubuntu (7.10 x64).

I've had the system lock up while using the partition editor to setup the install drives.  I've had the system lock up *during* the installation at several different points either during the formatting phase or at varying progress through the system install phase.  I've also had one instance where Ubuntu Live loaded up but it complained about numerous problems and it loaded up in Safe Mode, or something, I don't recall what.  But that's only happened once.

I then tried just booting into XP (the first OS on the drive) but GRUB would spit out "Error 17" and then lock up.  I booted into XP's recovery console and used FIXMBR and XP loads up fine now without any problems and I can use XP flawlessly.  But 7 out of 7 attempts this morning to install Ubuntu has been met with a system lock up.  The other thing that accompanies each freeze is the CAPS LOCK on my keyboard flashes as soon as the system halts.

I ran a check on the CD and it came up without any errors.  I would *really* like to be able to install Ubuntu; but as unfamiliar as I am with Linux I'm not sure where the problem is.  Especially since XP (installed on the first partition of the same physical drive) works completely fine.


[edit] When I first installed ubuntu Monday (the first and only successful install so far), it did so without a hitch at all; perfectly seamless. Then it crashed as I explained in the other thread (linked to above).

---

### Post by toastysquirrel on 2008-01-16
I'm not sure if this is related at all, but even when the LiveCD seems to be functioning well, when Partition Editor finishes its tasks successfully it will often crash upon completion.  All operations were successful, but it just dies at the end; but not always.

Still, my main concern is just getting Ubuntu to work.

:)

---

### Post by eolson on 2008-01-16
It could be a memory problem.   Reboot and spam the esc key.  You'll get the grub menu.   select the memtest option.  let it run for a few iterations.

---

### Post by EmoDx on 2008-01-16
I really think you have a bad hard drive. I don't know anything about linux, but with windoze the OS does a low level format prior to installation. Or, it will give you the option to.
Seeing how your system fails at different points, I would lean to your hard drive beeing bad rather than a bad install disk. I say this because your system can choose to write anything it wants to those portions of the hard disk, and because the drive actually sounds like the head is colliding with the platter. Can ya get your hands on a spare drive?

-E

---

### Post by sowelie on 2008-01-16
It definitely sounds like a hard drive problem.  You can run a simple test on the hard drive by booting with the live cd (do not do this in your regular install as running this test while the drive is mounted will make things worse).  Once booted into the live cd, open a terminal and type fsck /dev/sda1 (or whatever your hard drive is mounted as, if you have a regular ide drive it'll probably be /dev/hda1).  This will run a few checks and may give you some more information.

---

### Post by toastysquirrel on 2008-01-17
> **sowelie said:**
> It definitely sounds like a hard drive problem.  You can run a simple test on the hard drive by booting with the live cd (do not do this in your regular install as running this test while the drive is mounted will make things worse).  Once booted into the live cd, open a terminal and type fsck /dev/sda1 (or whatever your hard drive is mounted as, if you have a regular ide drive it'll probably be /dev/hda1).  This will run a few checks and may give you some more information.

Okay, so I did the above suggestion (after running memtest and Seagate's thorough drive diagnostics on the drive; both returning a clean bill of health).  As I ran FSCK on the drive it started spouting out a ton, literally dozens and dozens of errors along the lines of:

Inode 1016030 i_size is (lots of digits), should be 0.
Entry 'majongg.pyramid.scores' in /var/games (1015818) has deleted/unused inode 1016005
Inode blah blah has invalid mode...

and numerous entries with numerous other errors.

I tried running FSCK with the '-a' argument but it said "Unexpected Inconsistency"

Now I'm really confused because every diagnostic I've run, including in windows and running checks on the partitions from GPart all turn up a healthy drive.

Should I try the 32bit version of Ubuntu instead of the 64bit?  Should I just install it on another drive instead?  I'm not sure what to do.

---

### Post by Iowan on 2008-01-17
I had a hard drive that would do that - work all day IF it booted.  Occasionally it would come up w/ Inode faults on power-up and spend the next hour "repairing" things - after which I usually got to re-install.  Dunno if it was actually a bad drive - or drive parameters that were out of whack.  Replaced it and no more problems - so far.

---

### Post by sowelie on 2008-01-18
> Should I try the 32bit version of Ubuntu instead of the 64bit? Should I just install it on another drive instead? I'm not sure what to do.

I would recommend installing it on another drive if you have one.  Also, I find 32-bit to be a lot easier.  I had 64-bit installed for a while, but most packaged you find out there are in 32-bit, and there are still a few things that are annoying in 64-bit (flash player for example).  But you'll definitely want to get a new drive or install it on another drive if you have an extra one.

---

### Post by toastysquirrel on 2008-01-19
> **sowelie said:**
> I would recommend installing it on another drive if you have one.  Also, I find 32-bit to be a lot easier.  I had 64-bit installed for a while, but most packaged you find out there are in 32-bit, and there are still a few things that are annoying in 64-bit (flash player for example).  But you'll definitely want to get a new drive or install it on another drive if you have an extra one.

I'm pretty sure it was the drive after all.  I tried (dual-boot) intalling it on a separate drive but Gpart crapped out when it tried to assign a new label to the disk.  Next I tried a 40gb that I had laying around and everything seems to have gone through fine, including my adventures in trying to get the ATI drivers to work correctly.  From your statement above Sowelie, I might just try nixing 64-bit and going to 32, just to save myself some potential headache, I'm still totally new to this after all.  However this really depends on whether or not I stick with Ubuntu due to how installing packages is handled.

See further [query here]("http://ubuntuforums.org/showthread.php?p=4164496#post4164496"), if interested :)

---

