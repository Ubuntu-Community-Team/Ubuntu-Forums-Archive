---
title: "Mount NTFS Using Live CD"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-11-30
I would like to use a live cd (I have both Dapper and Edgy) to boot Ubuntu on a laptop running XP that is really messed up. It is so messed up that I cannot get the data off of it so I can reformat. I was hoping to use Ubuntu to access the Windows partition and then copy all the data onto an external HD. But then I forgot about the NTFS thing. 

Is there some way that I can mount this NTFS partition using the Live CD environment to get at my data?

---

### Post by taurus on 2006-11-30
Assuming it is the first partition of the first harddrive, /dev/hda1, open a terminal, Applications -> Accessories -> Terminal, and do

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows
sudo ls -la /media/windows
```

---

### Post by gigi1234 on 2006-11-30
Excellent, thanks!

---

### Post by cutlerite on 2006-11-30
> **taurus said:**
> Assuming it is the first partition of the first harddrive, /dev/hda1, open a terminal, Applications -> Accessories -> Terminal, and do

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows
sudo ls -la /media/windows
```

This worked, however I still can't access the information on my windows hard drive, or did it just erase it?

---

### Post by vanjagator on 2008-06-12
I just downloaded Ubuntu 5.10 Live CD and started on my laptop. I did the steps above and I can see my windows C: drive in the terminal window, but I cant access the files thru Places-Windows. It says I do not have permission necessary to view the contents of "windows". Im a complete Linux noob, but I need to recover some files from Desktop and My Documents folder really fast.

Any suggestions!?

I really need help :) 

Im totally desperate. Please!

I think it would be super cool if someone would reply! Mega cool!

---

