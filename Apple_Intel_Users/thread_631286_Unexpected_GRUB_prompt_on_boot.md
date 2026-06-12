---
title: "Unexpected GRUB prompt on boot"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by charleschoe on 2007-12-04
Greetings,
I am very new to linux and decided that Ubuntu is a great way to start.
I am running on a Macbook Pro (first gen) Dual-Core.  I am currently dual-booting with MacOSX 10.5.
I went through all the instructions and had ubuntu working fine.  I did a lot of simple modifications to get the DVD player to work, adjust fan speeds, and some other minor tweaks.

This morning, I booted Mac osx to work on my paper.  When i tried to restart and boot to Ubuntu, I get the GRUB prompt.  Now, i tried to google some answers and even search this forum for answers, but basically what's happening is that when I type "boot" in the GRUB prompt, I get an error.

Error 8:  Kernel must be loaded before booting.

I'm not too sure what to do, since I'm very new at all this.  I was thinking of just deleting the partition and installing fresh, but I went through that process countless times (before i got it working perfectly) because I simply did not know what to do when a problem arose.  

I'm thinking that when I booted into mac osx, it messed something up.  Even now, when I get into mac osx and look at the linux partition, it shows that there is nothing installed.    Please help :)

Regards

---

### Post by cyberdork33 on 2007-12-04
The problem you are getting would be consistent with the Ubuntu partition being erased (IDK why it would be, but it appears that it may be).

At the grub command prompt, use this command:
```
find /boot/grub/stage1
```
That should tell you if grub can open and read it's files on any partition.
If it returns a partition in the form of (hdX,Y) then you can just reinstall grub manually and it should work.
You can use this method:
[http://ubuntuforums.org/showpost.php?p=3890030&postcount=4](http://ubuntuforums.org/showpost.php?p=3890030&postcount=4)

---

### Post by charleschoe on 2007-12-04
When I type that in, I get another error.

Error 15:  File not found.

I'm guessing somehow the partition did get deleted.  Does this error simply mean that reinstallation is the only fix?

---

### Post by cyberdork33 on 2007-12-04
> **charleschoe said:**
> I'm guessing somehow the partition did get deleted.  Does this error simply mean that reinstallation is the only fix?
Most likely as it looks like the files are not on your partition anymore.
You can boot from the LiveCD and check them to see if there is anything actually on there before doing that.
If there is anything important that you have lost, then you might want to look into some data recovery utilities before doing anything to the partition at all.

---

### Post by charleschoe on 2007-12-04
Thanks again, you just saved me a couple hours of trying to find a fix for a lost cause.
Would you have any ideas of why this partition may have gotten deleted?  I haven't done anything but booted Mac OSX.  Everything was working fine up until that point.

---

### Post by cyberdork33 on 2007-12-04
> **charleschoe said:**
> Thanks again, you just saved me a couple hours of trying to find a fix for a lost cause.
Would you have any ideas of why this partition may have gotten deleted?  I haven't done anything but booted Mac OSX.  Everything was working fine up until that point.
I honestly have no idea. If the partition is completely blank, then I would guess it was formatted somehow. Something in OSX may have done it, but I am not sure what you did there, so there are any number of things.

How were you trying to access the Ubuntu partition from OSX?

Also, just FYI, the 'boot' command cannot be used in the grub commandline until you have specified a root and a kernel to load (similar to as is defined in /boot/grub/menu.lst)

---

### Post by charleschoe on 2007-12-04
> **cyberdork33 said:**
> How were you trying to access the Ubuntu partition from OSX?


Basically, all I did was open up the partitioned section of the hard drive from the Mac OSX desktop.  Similar to what I used to do when I dual booted windows through boot camp, and since it was formatted FAT32 I was able to transfer files back and forth.  But when I opened up the linux partition, no files were there.

---

### Post by cyberdork33 on 2007-12-04
> **charleschoe said:**
> Basically, all I did was open up the partitioned section of the hard drive from the Mac OSX desktop.  Similar to what I used to do when I dual booted windows through boot camp, and since it was formatted FAT32 I was able to transfer files back and forth.  But when I opened up the linux partition, no files were there.
Well, that is odd, because you usually cannot just open the linux partition in OSX, and it actually requires a 3rd party tool:
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

Well, good luck. I hope you have better luck in your later attempts.

---

