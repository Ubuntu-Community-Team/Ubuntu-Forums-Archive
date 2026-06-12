---
title: "Very quick Q, would appreciate a very quick reply, ty!!!"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-28
I tried to install ubuntu onto a desktop partition last night but it wasn't very successful. I partitioned the hdd 3 ways.

16gb for the OS (ex3 I think it was)
1gb for swap
100gb for my docs (which I put as ex3)

When it installed I could see the 100gb bit of harddrive on the desktop, could open it (it was already mounted) but I couldn't write to it!! grrr

So I re-formatted it to fat32 and got the same problem. I won't a seperate chunk of the hdd just for my docs incase I need to re-format ubuntu (incase I break it, lol).

What format do I need to format the other bit so I can access it easily with read / write access?

Thanks!!!

---

### Post by pseudonym on 2006-12-28
If you need to access these files from windows fat32 is the way to go. If not, any Linux filesystem should be fine. To be able to write as normal user to the area in question, you may need to change the permissions of the mount point. assuming this is called '/media/docs' , open a terminal and type - ```
sudo chmod 777 /media/docs
```
This will give universal access to at least the top level of /media/docs .

HTH

---

### Post by linuxbun on 2006-12-28
Na not for windows, it's for ubuntu users myself. WIll re-do that and try now, cheers :D

---

### Post by bigken on 2006-12-28
when you format the 100gig partition select it as your home partition ;)

---

### Post by linuxbun on 2006-12-28
Doh! that makes sense :rolleyes: :mrgreen: thanks for the quick replies :D

---

