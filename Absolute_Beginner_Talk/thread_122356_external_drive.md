---
title: "external drive"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by cmongini on 2006-01-27
had to reinstall the system because it always came up with error 18 and now i can´t write anymore to an external drive (vfat partition) i had no problems to access before....neither as root nor as normal user. the permissions of the drive are 700 i can´t see any way to change them (tried as root)...any hints? 
thanks

---

### Post by HJThis on 2006-01-27
Hi,cmongini

As far as i know you can try this but it maybe a 
good idea to post it here.

Open a terminal and type

sudo gedit /etc/fstab

Best of luck

---

### Post by cmongini on 2006-01-27
thanks, but i couldn´t do it... 
it is strange becz as soon as i put in the drive it would work. but the files that i wanted to put in had no write permission. i activated the write permission on the files ( chmod -R 777) and as soon as the files were OK the drive was not anymore ( the answer wasthat it is a read only device...)

---

