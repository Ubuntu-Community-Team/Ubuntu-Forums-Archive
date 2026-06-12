---
title: "Hide / Forbid Access to NTFS partition for certain users"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by flaxx on 2006-06-29
Hi everyone

I have a dual ubuntu/windows system. When guests use my computer, I would like them to use ubuntu (reasons are obvious) but they must not have access to certain folders of my NTFS partitions (or the whole partition) as they contain sensitive data.
I can't exclude those partitions in general from ubuntu (eg by modifying fstab) as MY ubuntu-account needs read-access to them.

Under Windows it's no problem as I'm set as the owner of the respective folders and the other accounts have no access.

chmod doesn't work as the NTFS filesystems are read-only.
 
How can this be performed?

Thanks for your advice
flavio

---

### Post by aysiu on 2006-06-29
I could be wrong about this (if I am, someone please jump in and correct me), but I believe this /etc/fstab entry lets all users read NTFS: ```
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
``` But something like this will allow only you to read it: ```
/dev/hda1 /windows ntfs ro,uid=1000,auto 0 0
``` I think *uid=1000* is your user ID (i.e., not other users' IDs).

That said, I think an easier way to have them not snooping there is not to make it obvious that your NTFS partition is mounted (mount it at some obscure location and don't make shortcuts to the desktop for it--except maybe in your account).

---

### Post by Apple 101 on 2006-06-29
Both options would probably give most assurance of non-readability...

---

### Post by aysiu on 2006-06-29
[QUOTE=Apple 101]Both options would probably give most assurance of non-readability...[/QUOTE]
Actually, I'm pretty sure the first option makes it read-only for *every* user. It's the second option I'm not too sure about.

---

### Post by Aurdal on 2006-06-29
I think he was reffering to the not making it obvious part as the second reason...

---

### Post by aysiu on 2006-06-29
Ah. That makes more sense than what I was thinking.

---

### Post by Jasper Houtman on 2006-06-29
The second one is the best. uid=1000 is your account, if other users log on with a different acount than they cannot mess with your NTFS volume.

---

### Post by uzi09 on 2006-06-29
well, if you only want a select few people, you could always create a new group, change the group that the NTFS partition belong to, and give them read/write access, while not allowing anyone else to read/write it at all.

---

### Post by flaxx on 2006-06-29
thanks guys I'll give it a try. Just installed i386 since Java and Flash didn't really work with the AMD64-k8 I had.
Off-topic: Does it only seem so or is firefox WAY slower in 32 than 64 mode? I noticed that before installing any extensions / plugins...

---

### Post by Apple 101 on 2006-06-30
[QUOTE=Aurdal]I think he was reffering to the not making it obvious part as the second reason...[/QUOTE]
Yes, I'm meant that... It just didn't come out that way...:p

---

