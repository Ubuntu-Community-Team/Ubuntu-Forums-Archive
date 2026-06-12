---
title: "At line for &quot;nfs sharing in rw,user&quot; in the /etc/fstab, is umask=000 required ?"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-26
(Just very newbie question)

---

### Post by Kapre on 2005-10-26
[QUOTE=patrick295767](Just very newbie question)[/QUOTE]

I dont think there would be a problem. I would give it a try and if there will be an error, I'll remove it then post the error here (so we'll all know)

K

---

### Post by patrick295767 on 2005-10-26
[QUOTE=Kapre]I dont think there would be a problem. I would give it a try and if there will be an error, I'll remove it then post the error here (so we'll all know)
K[/QUOTE]
 
 
Thanks a lot ... 
I tried with nfs in a shared folder from ext3 partition without umask=000 and I could do r/w normally ... (rw,user)
 
In fat32, I didnt try yet ... we'll see ...
 
Thank u

Patrick

---

### Post by markopolo12 on 2006-10-10
i've had similar problems gaining write access to my NTFS partitions. my umask is set to 0007 which is supposed to give r/w to users and groups but deny the "outside world". can't remember what my line in /etc/fstab is at the moment but i'll check it when i get home.

what do the rest of you have for mounting an NTFS partition in FSTAB that will give you both read and write access?

---

