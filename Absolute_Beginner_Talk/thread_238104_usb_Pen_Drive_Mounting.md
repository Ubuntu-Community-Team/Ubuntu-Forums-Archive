---
title: "usb Pen Drive Mounting"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by brownjl on 2006-08-17
Hi 

I am seeing a really strange problem and being fairly new I am unsure on how to diagnose it.

I have a script in my /etc/mkinitramfs/scripts/local-top folder called cryptoroot, its purpose is to mount my encrypted root partition, I am trying to use a pass key located on a usb pen drive.

Using the command
/bin/mount -t vfat /dev/sda1 /usb  

it is failing with an error 2, 

I have all the correct modules loaded and have the script drop to /bin/sh incase of error where if I the run the exact same command as above in this console it works first time with no errors.

I have a sleep 10 in my script too incase I am not giving the system enough time but I am at a loss now...

Cheers,

James

---

