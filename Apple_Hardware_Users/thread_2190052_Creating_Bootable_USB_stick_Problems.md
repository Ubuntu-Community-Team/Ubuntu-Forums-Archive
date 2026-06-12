---
title: "Creating Bootable USB stick Problems"
date: 2013-11-25
forum: Apple Hardware Users
---

### Post by mcmacker4 on 2013-11-25
Hi,
I am trying to create a new Bootable USB with the Ubuntu image but I can't. I've tried everything possible but the usb won't appear anywhere.
My mac is behaving very strangely and I don't know why. I've tried to format the USB stick to FAT, to Mac OS Plus (journaled), I've tried using GUID partition table or MBR but nothing works. Every time I try to put the ubuntu image file into the usb stick using the ```
sudo dd if=path/to/file.iso of=/dev/disk3 bs=1m
``` the terminal says it was successful but then the next step is to use ```
diskutil eject /dev/disk3
``` but it won't let me because there is nothing such /dev/disk3, it seems like the usb simply disappears or disconnects. If I unplug it and plug it back the computer tells me the usb stick is not readable. Even if I just leave it as if it was normal, the USB stick won't appear in either the mac's screen where you can choose the drive to boot from (press Alt while booting) or rEFIt.

Does anyone know what the problem is?

Thank you in advance.

---

### Post by oldfred on 2013-11-25
I do not know Macs, but this thread seems to have some good info.

       Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac
[http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630)

    
[h=2][/h]

---

### Post by mcmacker4 on 2013-11-25
Just tried that too, still doesn't work. ](*,)

---

### Post by mr1shaggy on 2013-12-01
Did you convert the .iso to a .img first? The dd command will only work with a .img.[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) That link will take you to a page that tells you how to do it for Ubuntu

---

