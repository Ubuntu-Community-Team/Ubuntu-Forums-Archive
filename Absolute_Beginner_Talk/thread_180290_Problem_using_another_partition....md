---
title: "Problem using another partition..."
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Daran on 2006-05-21
I dual boot Ubuntu and XP Pro right now.  I changed fstab to use the Windows' partition...  Options are ro and user. (yes, I wrote them as ro,user ....not actually as "ro and user" or anything like that).  Yet for some reason only root has permission to view the contents of it?  I have to open nautilus using sudo or open xmms using sudo to listen to some music files I have in Windows.


Does anyone have any idea why it only lets me do things as root even when I set it for all users?  Or does ubuntu for some reason have me use some other option?


Thanks....

---

### Post by aysiu on 2006-05-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Daran on 2006-05-22
Thanks.


Though he only mentions doing default which isn't that just ro and automount?  Along with only root being able to read?  What I want to do is make it so all users can read from it.

---

### Post by aysiu on 2006-05-22
If you follow the steps in that tutorial, all users will be able to read from it.

Windows partitions (NTFS and FAT32) don't follow the normal /etc/fstab rules, so it doesn't matter if you say it's ro or whatever. Their permissions are defined with umasks, as they don't support normal Linux permissions.

---

### Post by Daran on 2006-05-22
Ah, thanks, that worked.  Upon rereading it I saw that somehow (contacts falling out maybe? heh) I missed the part where he said to put in nls=utf8,umask=0222 in place of default......




So now it is read only and able to be used by all users?  Alrighty.



Question though....  What are the options of nls=utf8,umask=0222 though?


Thanks.

---

### Post by aysiu on 2006-05-22
[QUOTE=Daran]
Question though....  What are the options of nls=utf8,umask=0222 though?[/QUOTE] The first part has to do with the character encoding. The second part mounts it read-only for all users.

---

