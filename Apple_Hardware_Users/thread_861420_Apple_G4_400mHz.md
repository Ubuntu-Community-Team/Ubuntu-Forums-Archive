---
title: "Apple G4 400mHz"
date: 2008-07-16
forum: Apple Hardware Users
---

### Post by Ollie A on 2008-07-16
Hi,
I have an Apple Mac G4 400Mhz computer running with Ubuntu 6.06 on it.
Also, I have an Retail install copy of Mac OS 10.3.
I wish to install 10.3 on my computer but I know that it will not work by just putting in the disk.
On the internet I have read that I must:

1. Boot up computer
2. Log on and insert disk
3. Shut down computer
4. Turn on computer holding 'C'
5. Use the disk utility

Now I have no idea if this will work or not, seeing as I have no previous knowledge of installing Mac OSs.

Can anyone verify that this will work??

Thanks loads :)

-Ollie

---

### Post by rjcalifornia on 2008-07-16
> **Ollie A said:**
> Hi,

1. Boot up computer
2. Log on and insert disk
3. Shut down computer
4. Turn on computer holding 'C'
5. Use the disk utility

-Ollie

Yes, that´s pretty much it, hold the C when you turn on the mac. The Mac OS CD does everything. 

If your hard drive is not detected, then you use the disk utility. By the way, if you want to do a dual boot, you must use the disk utility of the cd and make two partition: One for mac (don't make any changes, leave the default) and another one for Linux (You must choose: Format as Free Space)

---

### Post by stream303 on 2008-07-17
Randy is right.  It would probably be easiest to start fresh and reinstall osx as the first os on the disk.  When firing up the osx installer, you may want to hit the top panel to fire up disk utility, delete all the partitions, and then just designate a partition for only half the drive for osx.  Leave the rest as free space.

Continue with the osx install, and when that is done, install Ubuntu to the free space.  Now yaboot will automatically discover the osx install and include it as part of your boot options.

---

### Post by Ollie A on 2008-07-17
Thanks guys for helping :)
Just wanted to make sure I don't muck it up!!

-Ollie

---

### Post by luke.is.very.handsome on 2008-07-17
If holding down the c key doesn't work for you and your computer keeps loading up linux, you can alternatively hold down the option key instead during the chime at boot.  This will being you to another bootloader that will let you click on the cd and then tell it to boot.  If it doesn't after that, you either have a disk that can't be read by that computer, or you need to completely erase the drive you are working on and get rid of all the linux stuff on it.  Some of these older macs are tempermental about installing osx back on to them, "some."

Good luck.

---

### Post by Ollie A on 2008-07-19
Thanks all!
Will let you know if it works next week because I haven't actually got the CD yet, and its posting from USA :(

Anyway, thanks!!

-Ollie

---

