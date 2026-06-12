---
title: "Changing file system type"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-28
I want to change my 2nd HDD which is NTFS into fat/fat32. How? I want to change it because I always have to mount it. I think fat/fat32 is better for me rather than NTFS.

---

### Post by xyz on 2006-11-28
More than one way to do it...
I like to use Gparted Boot CD. Read on it and follow the link to download here:
[A quick look at the GParted live CD]("http://www.linux.com/article.pl?sid=06/04/25/1917228")
Don't forget to back up your important data...

---

### Post by oliviacond on 2006-11-28
What if I want to change from NTFS into ext3. Is the changing can erase the HDD's data? If there's a way, I will be damn happy.

---

### Post by frodon on 2006-11-28
There's no way to convert a partition from NTFS without losing datas unfortunatly, so it would be better if you could find a way to backup your datas before the conversion.

---

### Post by oliviacond on 2006-11-28
I think the only way (because I don't have spare disk) is to create a new ext3 partition from the NTFS, and then move the NTFS's data to ext3 partition and then erase and kill the NTFS. Is it alright?

---

### Post by Sef on 2006-11-28
Any time you convert from one file system to another, the data will almost certainly be lost.

---

### Post by Abild on 2006-11-28
> **oliviacond said:**
> I want to change my 2nd HDD which is NTFS into fat/fat32. How? I want to change it because I always have to mount it. I think fat/fat32 is better for me rather than NTFS.
Have you tried mounting your NTFS partition with Captive NTFS or NTFS-3g to see if that does it for you?


> **frodon said:**
> There's no way to convert a partition from NTFS without losing datas unfortunatly, so it would be better if you could find a way to backup your datas before the conversion.

I believe Partition Magic is able to convert NTFS to FAT 32 but you'll have to buy it, and its windows only

---

### Post by oliviacond on 2006-11-28
no, i haven't use captive or 3g.

---

### Post by Sef on 2006-11-28
> Now I'm having problem with Gnomebaker when I want to burn the Gparted.
It says: Permission is denied

Right click on the icon and select burn iso.  If that doesn't work, the install K3b.  Applications > Add/Remove > search K3b

---

### Post by frodon on 2006-11-28
> **Abild said:**
> I believe Partition Magic is able to convert NTFS to FAT 32 but you'll have to buy it, and its windows onlyGparted do it as well and it's free but with both you will lose your datas and it's what is always annoying when converting a partition.

---

### Post by Sef on 2006-11-28
>  Originally Posted by Abild  View Post
I believe Partition Magic is able to convert NTFS to FAT 32 but you'll have to buy it, and its windows only

Also Partition Magic and Linux have not always gotten along.  GParted is a better choice both on price and quality.

---

