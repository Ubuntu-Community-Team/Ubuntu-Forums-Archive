---
title: "2nd harddrive"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by museleading on 2007-02-13
I got Ubuntu installed on my machine last night.  I then plugged in a second harddrive I want to use as storage.  It's a new harddrive, partitioned, but not yet formatted.

The BIOS found the harddrive, but Ubuntu did not.  I checked the device driver - there is a device listed for the second harddrive.

I checked the help file, which stated to click on admin, then discs.  I clicked on admin, but there was no disc menu option.

What should I do next to get Ubuntu to format & show the second harddrive?

---

### Post by taurus on 2007-02-13
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by tronica on 2007-02-13
well you need to format it, i use gparted, then you need to mount it, and add it to fstab so it will be mounted on each boot.

format it with gparted, then you need mount it like so,

> cd /mnt
> 
sudo mkdir drivename

> sudo chmod 777 drivename

> sudo gedit /etc/fstab

add

> /dev/hdb2 /mnt/drivename ext3 defaults 0 2

then just replace hdb2 with what ever that drive is labeled as.

---

### Post by museleading on 2007-02-14
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

a '>'

what's that mean?

---

### Post by museleading on 2007-02-14
> **tronica said:**
> well you need to format it, i use gparted, then you need to mount it, and add it to fstab so it will be mounted on each boot.

format it with gparted, then you need mount it like so,








add



then just replace hdb2 with what ever that drive is labeled as.


I tried that.

It came back with 

(yelp:8176): yelp warning **: Cannot find dbus bus
unmatched element: citerefentry
unmatched element: refentrytitle
unmatched element: citerefentry
unmatched element: refentrytitle

What's next?

---

### Post by cklinux on 2007-02-14
Hello everybody,

Thanks for the info it helped me too as I just formated my second hard drive who had xp and now I am only with Ubuntu on my system. :guitar:  
I have another question though is there a way to move my home directory on the new bigger drive or to mount it in a way that it will add the free space under my /home dir??
I tried mounting the new drive under /home but it resulted to loosing -temporarily- access to the old partition with home. Thanx for help.
Oh I have Edgy. All disks formated ext3.

---

