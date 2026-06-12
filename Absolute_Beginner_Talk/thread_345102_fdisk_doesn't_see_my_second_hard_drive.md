---
title: "fdisk doesn't see my second hard drive"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by pachipuro on 2007-01-23
This is kind of a strange problem.  I have sda1 as my primary drive and hdb as my second drive.  When I tried running sudo bash diskmounter I got "No usable windows/mac partitions found."  Also, fdisk doesn"t recognize it.  When I run it I get:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19670   157999243+  83  Linux
/dev/sda2           19671       20023     2835472+   5  Extended
/dev/sda5           19671       20023     2835441   82  Linux swap / Solaris

No hdb.  My device driver recognizes it, though.  It sees it as /dev/hdb.  My Knoppix cd mounts it automatically, and I was able to use diskmounter with my last computer.   Thank you for any clarity you can bring to this.  Also, my linux skills aren't well developed.

---

### Post by pachipuro on 2007-01-23
Sorry, I meant device manager.

---

### Post by mikewhatever on 2007-01-23
There is a similar question in a thread not too far away.
[http://ubuntuforums.org/showthread.php?t=345047](http://ubuntuforums.org/showthread.php?t=345047)

---

### Post by tonyr1988 on 2007-01-23
I had this exact same problem. This is how I solved it (I have no idea if it'll work in your situation, but it's worth a shot, right? :D):

1) When you're booting up and see the GRUB menu, go to the menu selection for Ubuntu and press the e key. You'll go to the edit menu.

2) You should see a few lines, like:

> title .....
root ....
kernel ...
initrd ....
etc etc etc

Scroll down to the kernel line and edit it (I believe you press the e key again....the bottom of your screen will help you navigate). At the very end of the line, add " ide=nodma". For example, my "kernel" line is the following (the stuff in the middle may be different than yours):

> kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash noapic nolapic** ide=nodma**

Then try your fdisk stuff again. 

NOTE: This isn't persistent - it will reset back to your normal settings after a reboot. If it works, you'll have to make it permanent by editing your /boot/grub/menu.lst file - if you need help with that (after you see that it works or not), I'll be glad to help.

Again, it's probably a small chance that it'll work...but that's what did it for me.

---

### Post by pachipuro on 2007-01-23
It worked!  I just ran diskmounter and it said, "Added /dev/hdb1 as '/media/hdb1'
."  Will restart now.

---

### Post by pachipuro on 2007-01-23
When I restart, hdb is in my media forlder, but I can't mount it.  So, yeah, it's not persistant.  How do I edit the /boot/grub/menu.lst file?  Got to run to work now.

---

### Post by Buck2348 on 2007-01-23
```
gksudo gedit /boot/grub/menu.lst 
``` The line is toward the bottom of the file.

Buck

---

### Post by pachipuro on 2007-01-24
Thanks, both of you.  I did both things.  Hdb1 is now in my file browser on the left, but for some reason it won't let me mount it.  It says, "unable to mount selected volume."  In fstab, it says, "#Added by diskmounter utility
/dev/hdb1 /media/hdb1 vfat rw,user,fmask=0111,dmask=0000 0 0."  On my last computer the icon showed on my desktop, but now, no.  Not sure what's going on.

This is from menu.lst:

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single ide=nodma
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

---

### Post by Buck2348 on 2007-01-24
I'm not the expert you probably need, but for what it's worth, here is a line from my fstab for a vfat disk:
```
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
```
Again, I have a lot to learn about these things, but I don't like the look especially of the entries  fmask=0111 and dmask=0000.  That looks like nearly no permissions to me.  You could change them to 0777 or use the umask like mine umask=007 and see if that helps.  Still, I don't think that's what's preventing it from mounting.  What do you get now from ```
sudo fdisk -l and 
df -h
```?

Buck

---

### Post by louieb on 2007-01-24
Two things make me wonder. The BIG one is that fdisk doesn't see the drive. 
and the second > and I was able to use diskmounter with my last computer.Did you just put the drive in a different computer?
If so did you make sure the jumper settings are  correct?
When you go into BIOS setup can you see the drive?
If you run fdisk in Knoppix does it see the drive?

---

### Post by pachipuro on 2007-01-26
Sorry for the long delay.  Because of the help from the first guy, fdisk now recognizes my second hard drive.  I tried umask, but that didn't help, I'm sorry.  I think, because fdisk now can see my second hard drive, it now becomes a standard problem, so I should be able to cruise the forums for information.  I want to thank everybody who commented.  This was my first time asking for help on the forums.  Everyone was very nice.  You have a great community here.  Thank you very much.

---

