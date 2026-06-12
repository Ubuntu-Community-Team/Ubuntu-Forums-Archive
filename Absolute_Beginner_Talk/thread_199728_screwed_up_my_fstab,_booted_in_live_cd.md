---
title: "screwed up my fstab, booted in live cd"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by jenphalian on 2006-06-19
I completely trashed my computer and started fresh with a "new" 40 GB hard drive I recycled from another old computer.  I wiped it, and installed Breezy from the CD, then did a dist-upgrade to Dapper.  I had everything working nicely, then went to add my slave drive to the mix.

I think I messed up the fstab entries I put in!  Now its hanging up when I try to boot it.  Looks like its hanging up when it tries to test the filesystems.  I'm booted in the live cd now - How do I get at my filesystem from the live cd??!  Any help would be appreciated...  #-o

---

### Post by b_martinez on 2006-06-19
I'm learning Kubuntu now, so this may not work.
If you can, boot into run level 2. Do this (I think) by typing the number 2 when you start the live Ubuntu CD. Wait for the boot up.
 IF your Ubuntu install is on the first hard drive, type in at the prompt 
mount dev/hda1 /mnt/hda1              <-------hit 'ENTER' key
chroot /mnt/hda1                               <--------again, hit 'ENTER' key
This chANGES root to the installed OS.
NOW type in 
init 5                                               
This starts runlevel 5 , the one most of us use, pictures, point-n-click, et&c.....
How to sudo or su - in this OS is somethiing I do not know, but if you do, now you can change the fstab file to work. Or just comment out the lines you put in ,and restart the computer.
HTH
Bill
p.s. hit the 'ENTER' key after typing in 'init 5'
B.

---

### Post by Xecuter on 2006-06-19
Could you paste your fstab-file here? Maybe you have something wrong in it.

---

### Post by irv on 2006-06-19
When you boot from the live CD you can mount your hard drive. I am not sure what your hard drive is hda, hdb etc. You might beable to boot to failsafe mode and edit your fstab file. There are other thread on this problem do a search and I believe you will find some answers.

---

### Post by jenphalian on 2006-06-19
I finally found where to get at the fstab file - I went to system>administration>disks manager, and from there I could see my drives.  Yay!

Anyway, my fstab was definitely wrong, here is what I just changed it to.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda6       /usr            ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hdb5     /media/hdb5     vfat    iocharset=utf8,umask=000 0 0
# /dev/hdb6     /media/hdb6     ext3    defaults        0       0

I commented the last two lines just to be sure I could boot it up.  I had them both set at "2" in the last column, now I've changed them to zero.  Don't know why I did that.

---

