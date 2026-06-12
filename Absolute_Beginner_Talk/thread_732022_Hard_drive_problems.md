---
title: "Hard drive problems"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by SINZAR on 2008-03-22
I just install a new hdd in my unbuntu machine that I had been previously using as a external drive on my windows machine. When I initially installed it, I could see the drive listed in places > computer but I didn't have read/write permissions on it so I used gparted and formated it. Now it's not being listed in places > computer and I can't access it.

It's not being listed in /etc/fstab but I can see it listed in /dev/disk

The unmount option is grayed out in gparted so I'm assuming its mounted but I'm not really sure what else to do to resolve this.

---

### Post by buntu_Geek on 2008-03-22
You should set a file system for accessing the hard disk space...
Not just formatting solves the problem...

Btw its not necessary to format for such a small problem... you could have solved it..... using ntfs-3g....

Anyways,,,
Now you have to set a type of file system.. to access the formatted partition..

---

### Post by Shazaam on 2008-03-22
Did you use gparted while booted to the livecd or were you logged into your Ubuntu installation?
Have you rebooted since making changes to the drive?
Is the drive a slave? Master? (jumper settings, plugged into the motherboard by itself, etc)

The safest way to make changes to drives is with your Ubuntu livecd or a similar app such as the gparted live cd. Using these live cd's make sure the drives won't be auto-mounted like they are in a normal Ubuntu install.

---

### Post by jan quark on 2008-03-22
let's have a look at your drives and partitions recognized by ubuntu

plase run in terminal and post the output

```
mount
sudo fdisk -l 
```

---

### Post by SINZAR on 2008-03-22
Well I feel silly, after a simple restart all is fine.

Thanks anyways though.

---

