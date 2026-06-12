---
title: "Hard drives"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by caramelsoul on 2007-03-10
First post on this site, and alas its a total n00b question. I have installed Ubuntu with no problems on my PC. It will be a dual boot PC with XP. The problem i have is that i dont seem to be able to see the other hard drives from my sytem. Well, i can see them in Device Manager but cant seem to access them. This is where i store my media files and i cant load my music into Rythmbox.

---

### Post by overdrank on 2007-03-10
> **caramelsoul said:**
> First post on this site, and alas its a total n00b question. I have installed Ubuntu with no problems on my PC. It will be a dual boot PC with XP. The problem i have is that i dont seem to be able to see the other hard drives from my sytem. Well, i can see them in Device Manager but cant seem to access them. This is where i store my media files and i cant load my music into Rythmbox.

If you are using dapper 6.06 you can go to system, system documentation and there is a good step by step instruction under desktop to mount your drives. Good luck!

---

### Post by raja on 2007-03-10
By default, the windows drives are automatically detected and are mounted in /media. Navigate there to see if your partitions are there. 
If not, you can give us the output of ```
cat /etc/fstab
``` to help troubleshoot.

---

### Post by caramelsoul on 2007-03-10
> **paul capps said:**
> If you are using dapper 6.06 you can go to system, system documentation and there is a good step by step instruction under desktop to mount your drives. Good luck!

I had downloaded 6.06 and 6.10. For some reason i chose 6.10. So that option isnt there...

---

