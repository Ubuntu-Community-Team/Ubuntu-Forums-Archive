---
title: "&quot;No room left on device&quot; when attempting to install Ubunto to a 1GB USB Thumb"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by tungsai on 2007-11-01
Hey, all.

Following the directions to a T, to the letter, etc., on this page:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

I get to the big hairy "cp" command, step 17, and before long, it's "No space left on device". 

df -h reveals,

/dev/sdb1             716M  716M     0 100% /media/ubuntu710
/dev/sdb2             267M  160K  253M   1% /media/casper-rw

100% full. Hmm. They DO recommend a 2GB drive, but... they say that 1gb should work... 

Any helpful advice?

~TungSai~

---

### Post by tungsai on 2007-11-01
PROBLEM SOLVED.

I was using the DVD ISO, not the "Desktop" ISO which is CD_ROM-sized.

however, my quest to succeed in making a ubuntu bootable thumb drive has so far still failed. I get no errors; but when it tries to boot, I get gobbledygook. I have gone through it 2x with no success.

The USB jump drive is a Lexar JumpDrive 1GB JDSP1g-04-500B

---

