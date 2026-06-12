---
title: "External harddrive problem"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Norway on 2007-05-09
Hi!

I have the same problem as this user [http://ubuntuforums.org/showthread.php?t=435289&highlight=external+harddrive](http://ubuntuforums.org/showthread.php?t=435289&highlight=external+harddrive) 
I did follow the instructions given, but It still doensn't work. Got any ideas what to do?

Greetings from Norway:)

---

### Post by Inxsible on 2007-05-09
Is the hard drive in NTFS ? If so you need to install ntfs-3g
 
Got to Applications -> Add/Remove and search for NTFS and install
That will allow you to write to those partitions.
 
The other problem could be that you might not have ownership over the external drive.
 
You can choose to assume ownership like so :
Go to Applications -> Accessories -> Terminal
```

sudo chown -R <your username> /<path to folder>

```
 
where the folder is the one on which you want to assume permission.
 
For eg. if you external HDD is mounted on /media/MyDrive and assuming your username is Norway
 
then it would be
```

sudo chown -R Norway /media/MyDrive

```

---

### Post by menard on 2007-05-11
Thanks a lot. I finally have write access to my external HDD (I completely removed XP a few weeks ago)

---

