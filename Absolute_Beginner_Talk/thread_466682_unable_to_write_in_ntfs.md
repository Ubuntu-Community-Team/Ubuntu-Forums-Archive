---
title: "unable to write in ntfs"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-06-07
even after installing ntfs-3g, I am able to read only. unable to write or paste in other partion. Single hard disk. dual booting

---

### Post by NeoLithium on 2007-06-07
Does the partition require root privilates to write onto it?  Run
```

gksu nautilus

```
And see if you can do anything with the partition that way.

---

### Post by Rocket2DMn on 2007-06-07
Applicactions -> System Tools -> NTFS Configuration Tool
Check the box that enables writing.

---

### Post by Inxsible on 2007-06-07
After installing ntfs-3g, Did you enable it by going to Applications --> System Tools --> NTFS Configuration Tool ?

Do you have permissions on the folder or drive where you are trying to write ?

---

### Post by drpas2k on 2007-06-07
> **NeoLithium said:**
> Does the partition require root privilates to write onto it?  Run
```

gksu nautilus

```
And see if you can do anything with the partition that way.

I tried and I got this reply. 

(nautilus:5804): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension



I am a single user. Home computer. Pl. advise

---

### Post by Inxsible on 2007-06-07
> **drpas2k said:**
> I tried and I got this reply. 

(nautilus:5804): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension



I am a single user. Home computer. Pl. advise

Dont worry about that warning. Its a harmless bug and has been reported. were you able to write to the partition in nautilus after that ?

---

### Post by Inxsible on 2007-06-07
opening nautilus in root mode is never a good idea. You should simply take ownership of the drive/folder that you want to write to.

```
sudo chown -R <your username>:<your group> <device path>
```

---

### Post by drpas2k on 2007-06-07
Thanks a lot. I am able to write.

---

### Post by NeoLithium on 2007-06-07
> **Inxsible said:**
> Dont worry about that warning. Its a harmless bug and has been reported. were you able to write to the partition in nautilus after that ?

Once this issue is resolved, you can get rid of the error message with the info from my post in this thread: [http://ubuntuforums.org/showthread.php?p=2612162](http://ubuntuforums.org/showthread.php?p=2612162)

---

### Post by Inxsible on 2007-06-07
Using gksu nautilus ?

It would be a good idea to change ownership then
post the output of ```
sudo fdisk -l
```

---

### Post by Inxsible on 2007-06-07
> **NeoLithium said:**
> Once this issue is resolved, you can get rid of the error message with the info from my post in this thread: [http://ubuntuforums.org/showthread.php?p=2612162](http://ubuntuforums.org/showthread.php?p=2612162)

Thanks NeoLithium. Got rid of an irritating but harmless message !!

---

### Post by drpas2k on 2007-06-07
> **Inxsible said:**
> opening nautilus in root mode is never a good idea. You should simply take ownership of the drive/folder that you want to write to.

```
sudo chown -R <your username>:<your group> <device path>
```

What is my group and how to give device path to all the pations of my single hard drive.

---

### Post by Inxsible on 2007-06-07
your group is more often than not your username unless you deliberately changed it.

you would have to give permissions on each of the partitions if you didnt already have them

---

