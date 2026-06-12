---
title: "changing owner on external usb hard drives"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by JerryParsons on 2008-03-12
I have four 500GB external hard drives that I plan to use for storing files to keep my laptop hard drive from filling up.  I have partitioned and formatted two of them as ext3 using GParted.  They both show root as the owner and I cannot transfer data to them.  I do have an old 120GB external USB drive that I can write to.  I have tried using "sudo chmod" from terminal with an assortment of parameters to no avail.  I have been working with computers for some time, but my UNIX experience was over 20 years ago and Linux seems very different.  How do I change ownership of the drives, and is there a parameter that can be set in GParted to establish the owner when a drive is partitioned and formatted.

---

### Post by sisco311 on 2008-03-12
```
sudo chown -R username:group /path/to/the/mount/point
```

---

### Post by justleen on 2008-03-12
you can change the ownership from a shell

```

sudo chown user:user /media/yourdisk -R

```
this will give group/ownership to user, on disk /media/yourdisk
the -R is for recursive.

---

### Post by andybleaden on 2008-03-12
I had trouble with this but got great help from member Taurus here which solved my problem

[http://ubuntuforums.org/showthread.php?t=696695](http://ubuntuforums.org/showthread.php?t=696695)

Note at the end I still had to go in via system settings and edit the ownership but all the commands enabled this to happen

---

