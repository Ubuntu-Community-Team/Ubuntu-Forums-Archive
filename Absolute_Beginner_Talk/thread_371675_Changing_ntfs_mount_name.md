---
title: "Changing ntfs mount name"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by TimJBart on 2007-02-27
I managed to get ntfs-3g working fine and both my NTFS partitions display on my desktop as I mounted them in /media

My only problem now is that they're named hda1  and hda5, whereas I'd rather they were called 'Windows' and 'Downloads'.

What is the easiest way to change this?  I am scared to touch anything in case I break my ntfs compatibility :) 

Thanks guys

---

### Post by taurus on 2007-02-27
Just change the names in /etc/fstab and don't forget to create the new mount points or they won't be able to mount at boot.  Then, reboot and you should all set.

---

### Post by TimJBart on 2007-02-27
> **taurus said:**
> and don't forget to create the new mount points or they won't be able to mount at boot.  

Would you be so kind as to remind me of which command that is?

Am I doing this to sort of create the space for my disks to fill :)  Once I have created their intended mount point, that setting will stay permanently?

---

### Post by taurus on 2007-02-27
To edit /etc/fstab, run this from a terminal.

```
gksudo gedit /etc/fstab
```
And to create those two new mount points, run

```
sudo mkdir /media/Windows /media/Downloads
```

And yes, they will mount to /media/Windows & /media/Downloads automatically each time you boot Ubuntu.

---

### Post by TimJBart on 2007-02-27
So you sort of create a space for things to be slotted into.  Then you actually slot them in.  The two are separate.  That seems a funny way of doing things to my brain but I will not question the wisdom of linux.  Am loving it so far...

---

### Post by taurus on 2007-02-27
Those are called mount points.  If you want to mount something in Linux/Unix, you need to have a mount point before you can mount to it.

---

