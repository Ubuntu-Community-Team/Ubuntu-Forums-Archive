---
title: "Mount Windows drive"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-09-27
How would I mount my windows harddrive. I want to copy a file from it to the linux drive but I am not sure how to mount it. When I go into Nautilus as root I still am unable to mount it. A GUI way would be the best for me but Command line is not bad either. Thanks for the help.

---

### Post by bodhi.zazen on 2006-09-27
```
sudo mkdir /mnt/windows
mount -t ntfs /dev/hda1 /mnt/windows -o umask=0000
```

You should now be able to access the windows partition with nautilus.

---

### Post by cptjaben on 2006-09-27
I found [this]("http://ubuntuforums.org/archive/index.php/t-1886.html") article to be helpful when I mounted my windows HDD's. Hope this helps.

---

### Post by PPAAUULL on 2006-09-27
How would I have it mount the partition Automaticly everytime I start the computer?

---

### Post by PPAAUULL on 2006-09-27
How would I know what to put in fstab to mount the partition automaticly?

---

### Post by bodhi.zazen on 2006-09-27
> **PPAAUULL said:**
> How would I have it mount the partition Automaticly everytime I start the computer?

Edit fstab. Now don't make this too complex. :)

```
sudo gedit /etc/fstab
```

Add this line:
> /dev/hda1  /mnt/windows ntfs auto,users 0 0

If you want read write access:

[[color=blue]How to NTFS[/color]](http://ubuntuforums.org/showthread.php?t=217009)

:cool:

---

### Post by PPAAUULL on 2006-09-27
Thanks I will try it

---

