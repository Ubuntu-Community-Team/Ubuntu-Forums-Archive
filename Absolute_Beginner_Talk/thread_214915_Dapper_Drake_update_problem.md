---
title: "Dapper Drake update problem"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by shiellb on 2006-07-13
This is the 3rd time this problem has occurred.  The first 2 times I was able to get someone to help me.  This time they are not available.  The problem is this:  after a large update, the cuomputer hangs up "waiting for root file system..."  after about 4 minutes the following message appears on the screen. 
Booting 'Ubuntu, kernel 2.6.15-26-686'
root(hd0,1)
 Filesystem type is ext2fs. partition type 0x83
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x1708a9]
initrd /boot/intrd.img-2.6.15-26-686
   [Linlux-initrd @ 0x1f949000, 0x6a658d bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kerenl.
ALERT! /dev/sda2 does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' fir kust if built-in commands.
/bin/sh: can't access tty; job control turned off
#

I forgot to ask the person who fixed it before to write down what they did.  He did mention that "/dev/sda2" should read "/dev/sda1".  He did change it and for some reason it changes back to "sda2".
What do I do to correct this problem myself?
Thanks.

---

### Post by slimdog360 on 2006-07-13
are you sure it says **s**da2 and not **h**da2
Im probably o the wrong track here but I thought that sda was the usb mounted devices and at that stage in the boot its looking at the hard drive(hda) and has nothing to do with the sb stuff. but again Im probably wrong here.

---

### Post by Rackerz on 2006-07-13
Do you have a usb device plugged in? Also did you update the Kernel by anychance?

---

### Post by shiellb on 2006-07-13
It reads just as I entered it:  ..."root-/dev/sda2 ro quiet splash"... and the rest of the info is the way I see it on my monitor.

---

