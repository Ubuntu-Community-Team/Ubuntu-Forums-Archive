---
title: "Hard Drive stopped working after installing Feisty"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Ian Goodrich on 2007-07-01
I just installed 7.04, my first distro upgrade (beams with pride) It helped solve a couple of other problems but for some reason my freecom external usb hard drive has stopped working. It whirs then stops repeatedly during the boot sequence and stops whiring altogether before login. The hard drive is then not recognised.

I'm very new to linux and know very little codewise. I'm running ubuntu on a Dell Inspiron 510m laptop. Has anyone got any idea what might be wrong?

Thanks

---

### Post by cmnorton on 2007-07-02
I have a usb drive, just plugged it into my Ubuntu system, and it auto-loaded. A window popped up showing the contents of the drive. The drive is labeled linux_image, and it's mounted on /media. Here's the information from /etc/mtab

/dev/sda1 /media/linux_image ext3 rw,nosuid,nodev 0 0

In other instances, I've created a root level mount directory, like /warehouse (for a terabyte usb drive we have), and then as root mount /dev/sda1 /warehouse, and that works.

---

### Post by Raineer on 2007-07-02
Just curious, what happens if you plug it in after everything has booted up?

---

### Post by eternalsword on 2007-07-02
in the terminal, run the following ```
ls -l /dev | grep sd
``` and post the results here

---

### Post by Ian Goodrich on 2007-07-02
Nah, it still doesn't work if I plug it in after I boot. 

Here's what I get after executing that command

crw-rw-rw- 1 root tty       2,  61 2007-07-02 17:55 ptysd
brw-rw---- 1 root disk      8,   0 2007-07-02 17:56 sda
brw-rw---- 1 root disk      8,   1 2007-07-02 17:25 sda1
brw-rw---- 1 root disk      8,   2 2007-07-02 16:56 sda2
brw-rw---- 1 root disk      8,   3 2007-07-02 17:56 sda3
brw-rw---- 1 root plugdev   8,  16 2007-07-02 16:56 sdb
crw-rw-rw- 1 root tty       3,  61 2007-07-02 17:55 ttysd

and my fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=40c067c1-71a4-45b9-b098-2d0368f6d11d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=F070F79D70F768AC /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=6316f663-9534-461e-bac3-be10f08a1105 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

It seems lots of people are having this problem, I can't get my head around most of the posts though. Any help would be greatly appreciated.. going back to windows is not an option.

---

### Post by annda on 2007-07-02
hmm, it looks like the external drive is sdb and the system sees it, bit doesn't see any partitions - there is no sdb1. could it be that the disk is unpartitioned? try gparted to see if the disk has partitions and ehat they are.

if that doesn't help, can you try it with another system - windows or the live cd - to see if the disk and its contents are ok?

---

### Post by Ian Goodrich on 2007-07-03
It works fine in Windows. I can't see it on gparted. Would like to get it sorted but I'm not very confident with the code. Contemplating switchin' to another distro.. not the best way to solve a problem though :(

---

### Post by eternalsword on 2007-07-04
what do you get from the command ```
lsusb
``` you should see your usb drive's manufacturer in that list if it's being detected correctly.

---

