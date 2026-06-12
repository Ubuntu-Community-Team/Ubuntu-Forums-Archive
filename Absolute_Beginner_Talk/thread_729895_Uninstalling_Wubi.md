---
title: "Uninstalling Wubi"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by treblechamp on 2008-03-20
I have just tried to uninstall Wubi from my System which is running vista. i removed the entry from add remove programs so that does not appear on the list anymore. The only problem is my HD is still missing 30gb which i allocated to wubi/ubuntu and i cant get this back. I have had a search on my C drive and found the following folder: wubi-save and the file BOOTSECT.BAK. Can somebody please help me to try to recover this missing drive space and make sure Wubi is gone from my system.

---

### Post by philinux on 2008-03-20
Have a look at the uninstall link.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by treblechamp on 2008-03-20
This unistall process does not seem vista friendly i am not sure where you go to edit the c://boot.ini       i used windows explorer to try and locate the file but it wont find it. Probably due to vista trying to hide all the admin stuff

---

### Post by treblechamp on 2008-03-31
Can anyone help with this as i am currently missing 30gb from my hd which has been allocated to ubuntu

---

### Post by NR1224 on 2008-03-31
did u use the 8.04 wubi or a different one?

---

### Post by treblechamp on 2008-03-31
The version which i had was 7.04.01 just cant seem to recover this missing space

---

### Post by knightcoder on 2008-03-31
The reason its not showing up is that vista does not recognize the Linux File system partition.
See, if you can see that partiton when you install a live cd (or a partition tool like partition magic).

---

### Post by mcduck on 2008-03-31
> **knightcoder said:**
> The reason its not showing up is that vista does not recognize the Linux File system partition.
See, if you can see that partiton when you install a live cd (or a partition tool like partition magic).

Wubi doesn't create a separate partition for Ubuntu but instead puts it into a file inside Windows file system..

---

### Post by forestpixie on 2008-03-31
> Wubi doesn't create a separate partition for Ubuntu but instead puts it into a file inside Windows file system.. Yea - I was under that impression as well - I read a similar thread a few days/weeks back and the general trend was to delete the file at the C:\

---

### Post by treblechamp on 2008-04-03
Hi I have searched for all wubi and ubuntu files on my system and deleted them but i am still missing 30gb. The wubi program does make a virtual partition for ubuntu but doesnt seem to want to let go.

---

