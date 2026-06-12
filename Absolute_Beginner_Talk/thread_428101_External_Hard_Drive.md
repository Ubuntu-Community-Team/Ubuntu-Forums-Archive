---
title: "External Hard Drive"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by jpboyes on 2007-04-30
I have a usb external hard drive. But i cannot eject it. when i try, it says "device cannot be ejected." i cannot figure out what is going on.

---

### Post by ZeroWing on 2007-04-30
Could ubuntu or it's swap have been installed on that drive?

---

### Post by jpboyes on 2007-04-30
no, i re-formatted it after linux was installed and i used a windows machine. It's formatted as FAT32.

---

### Post by Wake Rider on 2007-04-30
I have that exact same problem with my external 300GB NTFS hard disk. What I have been doing is just turning it off. That isn't recommended but at the moment I don't know what else to do and the data seems to be unaffected.

---

### Post by slumcat05 on 2007-05-01
This is a problem for a lot of us. Check out these threads:

[http://ubuntuforums.org/showthread.php?t=401591](http://ubuntuforums.org/showthread.php?t=401591)

[http://ubuntuforums.org/showthread.php?t=418688](http://ubuntuforums.org/showthread.php?t=418688)

Also, just unplugging the drive is a bad idea. There are a few temporary workarounds discussed in those threads, but the easiest (although annoying) aolution is to open a terminal and do:

```
sudo eject /media/usbdisk
```

where you substitute the location of your drive for /media/usbdisk. Although the "right-click > eject" does not work, this should. Hopefully an official fix will be posted soon for this, but for now, this will be better for your drive than just unplugging it.

---

### Post by drascus on 2007-05-13
I have had this same problem with my Western Digital hard drive. I have come up with a sort of compromise solution. this does make it so you don't have to enter a command every time though. 
First: right click on the your top panel and click "add to panel" second: click "custom application launcher" then add these values :type: Application in Terminal; Name: eject; 
Command: sudo eject '/media/whatever the name of the disk is' ; comment ejects disk .  don't forget when doing the command to include the ' ' symbols at the begging and end of the location to be ejected other wise it will not work. when you click on the launcher it will open terminal then just enter your password and it will eject the volume. I hope this helps 
~Drascus~

---

