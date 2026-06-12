---
title: "Udpate backups"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by dosmode on 2007-03-05
I on my umteenth install of ubuntu due to the fact that I am new to linux and I am in the learning/experimenting/fiddling around stage... and would like to know if there is a way to backup the updates, to a CD preferably, which normally take a couple hours to download.  Everytime I do a clean install there are something like 150 updates and it would be nice if I could back these up somehow/somewhere so that I may update from that source instead of from the internet which would save me a lot of time.

---

### Post by chewearn on 2007-03-05
See this link:
[http://ubuntuforums.org/showthread.php?t=233486](http://ubuntuforums.org/showthread.php?t=233486)[URL="http://ubuntuforums.org/showthread.php?t=233486&highlight=backup+updates"]
[/URL]

---

### Post by dosmode on 2007-03-05
Thanks, AstalaVista... I appreciate it...  Hasta la vista....

---

### Post by dosmode on 2007-03-05
Okay... I tried burning these files to a CD but I have not been able to due to a "lock"file in the /var/cache/apt/archives folder... I am wondering what is the significance of this file and should I just skip burning this file to the CD since I am presented with that option... Thanks...
Another question... can I burn these files to CD under Windows platform and if so will they be "usable" under LInux OS...? Again, thanks...

---

### Post by chewearn on 2007-03-05
> **dosmode said:**
> Okay... I tried burning these files to a CD but I have not been able to due to a "lock"file in the /var/cache/apt/archives folder... I am wondering what is the significance of this file and should I just skip burning this file to the CD since I am presented with that option... Thanks...

You just need the deb files.

> Another question... can I burn these files to CD under Windows platform and if so will they be "usable" under LInux OS...? Again, thanks...

Should not be a problem to use Windows to burn the CD.

Depending on your situation, it might be easier to either:
1. use a flash drive
```
sudo cp /var/cache/apt/archive/*.deb /media/usbdisk
```

2. use a separate data partition

---

### Post by dosmode on 2007-03-06
Thanks astalavista... the archive folder has grown to more than 400 megs and would hate to have to download these files again...

---

### Post by xfile087 on 2007-03-06
Nice tip guys!

---

