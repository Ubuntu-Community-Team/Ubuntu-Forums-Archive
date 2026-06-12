---
title: "Problem playing video"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-05-22
I am having problems playing .avi files in Mplayer that are stored in a directory that is shared through samba (ex. smb://etc/etc/video.avi). If I try to play an .avi file that is on the same filesystem works flawlessly. Any ideas?? work arounds??

---

### Post by taurus on 2007-05-22
Have you mounted it somewhere first with smbfs?

---

### Post by adt41287 on 2007-05-22
yes, it is mounted on the system it is being shared from.

---

### Post by taurus on 2007-05-22
Where did you mount it to?  Can you access those videos either from a terminal or with nautilus?

```
df -h
```

---

### Post by adt41287 on 2007-05-22
it is mounted at /media/sda1 
i have access to them thru nautilus, but have not tried the terminal.
i am at work right now, so i am not able to mess with anything now

---

### Post by taurus on 2007-05-22
If you can see those videos with nautilus, then you can play them with mplayer.  Assuming the path to them is /media/sda1/Shared\ Documents/Movies, open a terminal and run

```
gmplayer "/media/sda1/Shared Documents/Movies/filename.avi"
```

---

### Post by adt41287 on 2007-05-22
> **taurus said:**
> ```
gmplayer "/media/sda1/Shared Documents/Movies/filename.avi"
```

if i were to do that command on the remote computer, wouldnt "/media/sda1/Shared Documents/Movies/filename.avi" point to its own /media/sda1/blahblahblah rather than the remote shared folder?? or is that not how it works?

---

