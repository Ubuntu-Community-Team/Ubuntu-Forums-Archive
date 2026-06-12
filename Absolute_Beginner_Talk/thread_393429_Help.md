---
title: "Help"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Audrokit on 2007-03-25
I installed Ubuntu 6.1 on a 10gb partition which i created on my laptop, however, it has now installed on the d drive but it only boots from there and doesn't use the acronis boot manager for me to select the operating system... can anyone tell me how I can get Win XP to boot as the primary boot again???

How can I configure the Grub to boot back to XP as the primary boot??

---

### Post by Kamu on 2007-03-25
You should be able to hit a key during the grub bootloading stage to go to the operating system selection menu.  You should be able to get Windows (it may be called "Other") from there.  To make Windows the default booting OS you can try the following... 
In an ubuntu terminal

cd /boot/grub

make a backup copy of your menu.lst file:  cp menu.lst menu.lst.backup
open menu.lst to edit: sudo emacs menu.lst

near the bottom of the file you should have a list of kernel and OS options.  For example mine has entries like:
  title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

Just identify the one that corresponds to Windows and move it to the top of the list.

Now playing with the bootloading file can be a bit dangerous, I recommend you make sure that you know how to access the manual selection in grub (which if I remember is by hitting enter or escape when grub is showing up during bootup) before you start editing the menu.lst file.  for extra safety, backup important files.

---

### Post by Kamu on 2007-03-25
Mmmm... I just re-read your post... my answer assumes you are indeed using grub as your bootloader.  I do not know how acronis works.

---

### Post by ThrobbingBrain66 on 2007-03-25
I've read that just moving the entries around in menu.lst isnt the best idea.  I believe that if you do that and then grub is updated it can mess up menu.lst pretty bad. At the beginning of  the menu.lst file is a section that looks like this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0
```

To make XP your default boot choice, change the number 0 to whatever partition corresponds to your XP install.  Remember that partitions start at 0 however, so 0 is actually the first partition.

EDIT: Opening a terminal and typing ```
cat /etc/fstab
``` will list all your partitions.

---

### Post by Kamu on 2007-03-25
What he says.  It sounds like a better idea... (*takes mental note to modify that on her dual boot system when she gets home*)

---

