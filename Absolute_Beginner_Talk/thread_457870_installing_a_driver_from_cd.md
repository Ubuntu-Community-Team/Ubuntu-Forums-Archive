---
title: "installing a driver from cd"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-05-29
Hi - I installed Ubuntu server - which unless i did something wrong does not install with a GUI ??
anyway i now know how to down load this GUI if only i could get an internet conection !!!

i have found a driver for my 3com card and burnt it to a cd rom ---


what i cant work out is how to access the cd drive from terminal mode ???


I do not have a GUI ....



any helpers ???

---

### Post by justleen on 2007-05-29
you try installing the GUI with the following command :
```
 sudo apt-get install ubuntu-desktop 
```

---

### Post by lupgop on 2007-05-29
that wont work as i need to install the driver for the network card...
i cant work out how to mount the cd drive 
tried mount dev/cdrom mnts/cdrom 

etc...
comes up with messages like no such file...
what the best book for command language rather than gui ??

---

### Post by mozetti on 2007-05-29
You need a mount point to mount any drive. Assuming you didn't have a typo, I don't think the mount point you used exists:```
mnts/cdrom
```

It is **mnt** and not mnt**s** -- so confirm that the mount point exists first. ```
cd /mnt
ls
```

Is there a **cdrom** file or directory listed? If so, then just ```
sudo mount /dev/cdrom /mnt/cdrom
```

If it isn't listed, then (while in the /mnt directory) ```
sudo mkdir cdrom
```

And then run your **mount** command.

---

### Post by lupgop on 2007-05-29
does it not need to know the location of the cd drive -- i read somewhere about IDE beinh hda,hdb,hc and hdd ??  if i use    sudo mount/cdrom  how ill it know which cdrom ???

---

### Post by mozetti on 2007-05-29
Yes, the location of the cd drive is ```
/dev/cdrom
```

If you have more than one cd drive, then you need to specify the correct drive. But, all your drives/partitions should be listed in the /dev directory. For example:
```
/dev/cdrom
/dev/cdrom1
/dev/hda
/dev/hda1
/dev/hda2
/dev/hdb
/dev/hdb1
/dev/hdb2
```

So, in the **mount** command I gave above, you're saying -- "mount the drive/partition located at /dev/cdrom at the mount point /mnt/cdrom".

---

