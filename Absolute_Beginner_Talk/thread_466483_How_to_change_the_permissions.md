---
title: "How to change the permissions"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by fengjing99 on 2007-06-06
Hi!
I got a external drive to backup my internal hard drive. However, I cannot write any file from the internal hard drive to the external hard drive. I can only read them. I logged in the Ubuntu 7.04 with administrator's account. Any body has any idea of changing the permissions? Thanks!

---

### Post by bren on 2007-06-06
it might me permissions.....

but it might be that you external drive is formatted as NTFS.

ubuntu can read NTFS by default

to write to it you need to go applications / add-remove / and search for NFFS-3g

Install it and you are up and running.....

good luck

bren

ps if it is permissions then you want to use the chmod command (wiki search for it)

---

### Post by fengjing99 on 2007-06-06
Thank you Bren! It is the NTFS problem. Now I got a FAT-32 external hard drive. It worked perfect.

---

### Post by bren on 2007-06-06
good!

by the way i had a typing error in my first post

install NTFS-3g not NFFS-3g and the NTFS one will work too

bren

---

