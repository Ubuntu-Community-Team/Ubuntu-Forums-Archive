---
title: "External NTFS USB drive"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by CyberDean on 2008-03-22
I have a Gateway PC running dual boot Gutsy and XP.  I have an internal drive partitioned 100GB for each OS, and an external USB 250GB drive formatted NTFS.  Everything runs great and smooth for both drives on both Os's except for about 1 out of 10 power ups.  Still no problem accessing the external drive, but in Gutsy I get two icons on the screen for the external NTFS drive once in a while, about 1 out 10 boot ups.  If I unmount one of the icons the drive is gone but the other icon still remains.  These boot ups are not restarts, but cold power ups.

Why would two icons appear about 1 out of 10 power ups?  And how can I correct this?

Thanks.

---

### Post by jan quark on 2008-03-22
hm 
can you post your fstab file
```
cat /etc/fstab
```

---

### Post by CyberDean on 2008-03-22
Nerver done a screenshot before, working on it.  I have the screenshot on my desktop, but can't figure out how to get it on this reply.:confused:

---

### Post by jan quark on 2008-03-22
when you click on post reply, scroll down and click on manage attachments
then upload the picture and submit your replay

a good tool for making a screenshot of the desktop is ksnaphot

---

### Post by CyberDean on 2008-03-22
I'll give this a try.

[http://ubuntuforums.org/attachment.php?attachmentid=63455&stc=1&d=1206220127](http://ubuntuforums.org/attachment.php?attachmentid=63455&stc=1&d=1206220127)

Cool,it worked, THANKS. Learned something new today.

The USB external drive is not listed, it's mount point is /media/NDAS.

---

