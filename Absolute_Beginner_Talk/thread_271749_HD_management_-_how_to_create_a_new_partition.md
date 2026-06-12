---
title: "HD management - how to create a new partition"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by robin.w on 2006-10-05
Hello everybody here,

I would like to creat a new partition. Anyway stricly speaking I want to divide the NTFS partition such to do not loose my WinXP and other data. I need a similar utility like Partition Magic. 

Does anybody know how to do that in Ubuntu???

---

### Post by Crooksey on 2006-10-05
Sure :-)

[http://qtparted.sourceforge.net/download.en.html](http://qtparted.sourceforge.net/download.en.html)

---

### Post by JGuru on 2006-10-05
Install the package **Gparted**, Open the Terminal Window & type:
 It can resize, delete, create partitions including NTFS. 
 $ **sudo apt-get install gparted**

  After the installation is complete, type this command to launch **Gparted**.

 $ **gksu gparted**

---

### Post by LookTJ on 2006-10-05
boot livecd, open terminal,

type in terminal

```
sudo gparted
```

---

### Post by cotcot on 2006-10-05
First of all, before you touch your ntfs please defragment it.
Then make a backup. I suggest to learn about "partimage" if you do not know it. It allows backup and restore of a complete partitions.
I fully agree with using gparted or qtparted, but by preference from the GParted LiveCD. The ubuntu gparted is not working perfect.

---

