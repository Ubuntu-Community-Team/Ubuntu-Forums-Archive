---
title: "Mounting a network drive on boot"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by mells on 2007-02-02
Hi 

How do you automatically mount a network drive? 

In Windows I can map my Network Attached Storage device. In Ubuntu it doesn't want to play.

I have created a Windows Share (File > Connect To Server > Windows Share). I can access the drive but I cant open anything.

The drive I want to have access in Ubuntu is FAT32.

Please help.

---

### Post by mells on 2007-02-02
anyone?

---

### Post by jordanmthomas on 2007-02-02
make sure you have smbfs installed.

Then, you'll want to edit /etc/fstab and add your share

```
//winbox/share  /mnt/share  smbfs username=joe,password=bloggs,uid=500,gid=500 0 0
```

This is the general format.  You will need to modify it to your standards of course.

[http://wiki.linuxquestions.org/wiki/Samba](http://wiki.linuxquestions.org/wiki/Samba)

---

