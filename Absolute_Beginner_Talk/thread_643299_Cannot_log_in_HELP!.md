---
title: "Cannot log in HELP!"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by H3retic on 2007-12-17
Okay, so as I do, I made many modifications to my ubuntu, most which I don't remember.  
My problem is, when I log into Ubuntu, I'm left hanging when it loads the desktop (I disabled the login screen through Administration>login Window - I go directly into the desktop) with the wallpaper showing up, but nothing else.

If I use a live CD to try to recover the data, Linux's famous security stops me from copying files onto my thumbdrive.

I need a way to access the desktop to recover my files (pictures, documents, etc).  How do I do this?

Help!

---

### Post by jken146 on 2007-12-17
If you copy things as root in the live CD you will not be met with any permission problems.  Just preface your terminal commands with **sudo** or, to use the file browser, ```
gksu nautilus
```

---

### Post by marcopolo1981 on 2007-12-17
Hi.
I have modified ubuntu quite a bit, which - being a newbie - means I make lots of mistakes! If I go one step to far and can't boot, I swap my internal and external drives. Reinstall ubuntu on the internal then copy all the pics, music and stuff from the external via usb. I think this quite a crude, long winded method and someone will probably tell you a better way. But maybe, if all else fails, you can try it.
Mark

---

### Post by H3retic on 2007-12-17
When I use *gksu nautilus* it only shows the live cd filesystem.  Is there a way to make it show the computer's filesystem as well?

---

### Post by marcopolo1981 on 2007-12-17
> **jken146 said:**
> If you copy things as root in the live CD you will not be met with any permission problems.  Just preface your terminal commands with **sudo** or, to use the file browser, ```
gksu nautilus
```

thanks jken. I can use that too!

---

### Post by napoleon3665 on 2007-12-17
well if u have ur pc dualbooted with something like vista, i believe tht u can access ur ubuntu partition there, of course, this is useless if u dont have 2 os's

---

### Post by H3retic on 2007-12-17
> **napoleon3665 said:**
> well if u have ur pc dualbooted with something like vista, i believe tht u can access ur ubuntu partition there, of course, this is useless if u dont have 2 os's

I found two things that might help

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html) = Driver to read/write ext3 in Windows

[http://rs286.rapidshare.com/files/77275551/ext2.exe](http://rs286.rapidshare.com/files/77275551/ext2.exe) = Program to read only ext3 in Windows

I'll try that

---

### Post by jken146 on 2007-12-17
> **H3retic said:**
> When I use *gksu nautilus* it only shows the live cd filesystem.  Is there a way to make it show the computer's filesystem as well?

Well, any partitions on hard disks should get mounted automatically be the live CD.  But if they don't, you need to do the following:

1.  Open up a terminal and type ```
sudo fdisk -l
```
This will show you your partitions, like this: ```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa06aa06a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7133    57295791   83  Linux
/dev/sda2            7134        7296     1309297+   5  Extended
/dev/sda5            7134        7296     1309266   82  Linux swap / Solaris

```

2.  Choose the partition(s) you want to access.  For each one, let's say /dev/sda2 in this case, you must first create a mount point and then mount it.

3.  Create a mount point (this is just an empty directory):  ```
sudo mkdir /mnt/sda2
```

4.  Mount the partition:  ```
sudo mount /dev/sda2 /mnt/sda2
```

5.  To access the files in a file browser, use ```
gksudo nautilus /mnt/sda2
```

*Of course, replace **sda2** with whatever partition you want to use.*

---

