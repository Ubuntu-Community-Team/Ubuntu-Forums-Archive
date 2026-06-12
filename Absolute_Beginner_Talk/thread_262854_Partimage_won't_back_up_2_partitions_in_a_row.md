---
title: "Partimage won't back up 2 partitions in a row?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-22
Hi everyone,
I backed up both my Windows Home and Dapper to my /media/usbdisk and /media/usbdisk-2 respectively. All went well guided by:
[Psychocats/Partimage]("http://www.psychocats.net/ubuntu/partimage")

Basically you boot on Ubuntu's Live, edit your /etc/apt/sources.list and uncomment universe/multiverse and run:
```
sudo aptitude update && sudo aptitude install partimage
```
This will not hurt your system since you're working off the Live CD.
```
sudo partimage
``` to open it.
For more see Psychocats link.

My question is this: I backed up Windows and wanted to immediately proceed to backing up my Ubuntu but it wouldn't!
I had to reboot on the Live CD and go through the whole procedure again. No big deal...but anyone knows why this is happening and if it can be avoided?
Thanks.

---

### Post by chrisfay on 2006-09-22
That's strange...I use partimage to run multiple consecutive backups nightly. Have you tried installing partimage on your system beforehand rather than durring your live session? Then just start it from the live cd...

---

### Post by xyz on 2006-09-22
> Have you tried installing partimage on your system beforehand rather than durring your live session?

No I haven't but I don't understand how this could fix it since working off the Live CD is totally independant from the installed OS.
But it is strange...perhaps someone will come up with an explanation.

Maybe it's simply not possible running off the Live CD!!!

---

### Post by chrisfay on 2006-09-22
> No I haven't but I don't understand how this could fix it since working off the Live CD is totally independant from the installed OS.

True...:p 

> Maybe it's simply not possible running off the Live CD!!!

I know its possible; I run my nightly backups with partimage using knoppix.

---

### Post by xyz on 2006-09-22
I haven't because I don't really need to back up as much but it may be interesting for you to schedule backups!!

[rsync and tar]("http://www.ubuntuforums.org/showthread.php?t=240326")

---

### Post by chrisfay on 2006-09-22
I actually do both. I tar my fs nightly to a samba share through cron and manually reboot into my knoppix live disk to create parition images as well. I am pretty paranoid I guess, but better safe than sorry.

---

### Post by xyz on 2006-09-22
> better safe than sorry.
You're absolutely right there!

---

