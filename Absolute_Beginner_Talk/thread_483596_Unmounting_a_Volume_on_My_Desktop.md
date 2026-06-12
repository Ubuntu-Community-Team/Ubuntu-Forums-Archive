---
title: "Unmounting a Volume on My Desktop"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Carnage_7 on 2007-06-24
I need to unmount one of the volumes that is showing up on my Ubuntu desktop.  However, when I right click the volume and then click on Unmount I get an error message that only Root can unmount the volume.  I am a newbie to Ubuntu.  How do I unmount this volume?  Thanks

Frank
El Paso, Texas

---

### Post by ajmorris on 2007-06-24
> **Carnage_7 said:**
> I need to unmount one of the volumes that is showing up on my Ubuntu desktop.  However, when I right click the volume and then click on Unmount I get an error message that only Root can unmount the volume.  I am a newbie to Ubuntu.  How do I unmount this volume?  Thanks

Frank
El Paso, Texas

Press Alt+F2, then type sudo nautilus. Navigate to the File System, then go to media... right click on the volume you want to unmount and click unmount. That should do the trick :)

---

### Post by Happy_Man on 2007-06-24
Assuming that the volume is mounted in /media/sda1, and that the HDD is known as /dev/sda1.... 

Open a terminal and type this:

```
sudo umount /dev/sda1
``` 

If you have no idea what I just said, post back. :p

---

### Post by Carnage_7 on 2007-06-24
Thanks-I was able to unmount the volume using the command provided sudo umount /dev/sda3.  I tried the other method suggested but when I right-clicked on the volume I was not given the option to unmount the volume.

Frank
El Paso, Texas

---

