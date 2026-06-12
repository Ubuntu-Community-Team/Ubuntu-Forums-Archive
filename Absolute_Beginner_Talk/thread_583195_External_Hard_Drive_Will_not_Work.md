---
title: "External Hard Drive Will not Work"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ccorona1 on 2007-10-20
Hi Everyone,

I a very new to the linux world (I just decided to take the plunge with Gutsy).  I have a laptop which was running XP.  I backed up my important files on a Seagate External 250 GB USB hard drive, and then installed Ubuntu (no dual boot, just one partition).  I am now trying to access my external hard drive, but ubuntu does not seem to be "seeing" it.  I have a USB flash disk that works fine, but nothing happens with the hard drive.

How can I get my hard drive to work so I can access my important files?  Isn't Gutsy suppose to "just work"?

Need help!

Thanks!

---

### Post by Qwerty_ on 2007-10-20
I assume that your external drive is running NTFS. In which case you need to install a special tool to configure your Ubuntu to read NTFS partitions

```
sudo apt-get install ntfs-config
```

Then run ```
 sudo ntfs-config
```

And select the external drive.

---

### Post by Pumalite on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by ccorona1 on 2007-10-20
Qwerty,

I did that, and I checked the "enable write support" box, but still nothing.

Any other ideas?

---

### Post by ccorona1 on 2007-10-20
Actually, sudo fdisk -l is telling me it is fat32?

---

### Post by Qwerty_ on 2007-10-20
So in effect you can see the drive then. But cant access the contents of it.

---

### Post by ccorona1 on 2007-10-20
Yes, it appears that way.  Any thoughts?

---

### Post by ccorona1 on 2007-10-20
*bump*

---

### Post by Delvien on 2007-10-20
Add "Disk Mounter" to your panel and see if the USB HDD is available, if so left click it and hit "Mount XXXX"

---

### Post by ccorona1 on 2007-10-20
Like I said I'm a bit new to ubuntu, how do i go about adding disk mounter to my panel?

---

### Post by Makrie on 2007-10-20
> **ccorona1 said:**
> Like I said I'm a bit new to ubuntu, how do i go about adding disk mounter to my panel?

Hey! I've just done this myself. 

Right click on the panel (across the top of the screen by default).

Go down to 'Add to panel' (the top choice?) and click it.

In the third section (System & Hardware) you see Disk Mounter - drag this to the top panel.

Done!

Good luck!

---

