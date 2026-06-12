---
title: "how large a partition for ubuntu"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by chazzjazz on 2005-11-09
whats the standard size partition for basic webbrowsing and openoffice

---

### Post by Samuel on 2005-11-09
i would go for around 4gb if i knew i wasnt going to be saving any amount of files on it.

---

### Post by zerhacke on 2005-11-09
I have a Ubuntu setup sitting on a four gig drive, using the entire drive, and havn't had any complaints yet.

Most of my machines have 40 gigs allocated to Ubuntu, but this machine is for my daughter.  She does nothing but go to barbie.com and nickjr.com.  She doesn't need any download space, so she got the old drive sitting in my closet.  In short, if all you're going to do is surf and not download anything, 4 gigs is plenty of space, and you could probably get away with less.

---

### Post by venzen on 2005-11-09
Yep, about 4gb is good.

consider this partitioning scheme:

/          3gb
/home   1gb
swap     512    (or at least 1 and a half times the size of physical RAM installed)

Also, if your pc is slower than 500mhz try installing xfce4 desktop environment instead of gnome.

---

### Post by Herman on 2005-11-09
It's very much a matter for individual preferences as to how many GB you need for a partition to install Ubuntu on. It depends on how you want to use your computer and how much spare disk space you have at your disposal, and what your other exsiting partitions are.
Web browsing will not likely take up any disk space, if you only wanted to do that, and not download anything or receive any e-mail, then the smallest you can install 'Breezy' on is around say 2.0 GB. My 'System Monitor' on a fresh basic 'Breezy' test  install which I'm typing from now from says 1.60 GB used (out of 10.0 GB). But not too many people would really like being that resticted for long.
I'd think between 5 and 10 GB would be more a more realistic suggestion for most people if they have a modern computer with the size of hard disks commonly around nowadays. Say 10.0 GB would give you room for files such as you might create with open office .org and other apps, as well as some e-mails and downloads etc. You can increase the size of Ubuntu at a later date. 10.0 GB would be  a good general starting point for most people.

---

### Post by chazzjazz on 2005-11-09
I need to dual boot with windows on a a couple of scsi drives....are RAID working on linux??

---

### Post by towsonu2003 on 2005-11-09
/ 4,5 gb
swap = RAM * 2 MB
/home rest of it

have no idea about RAID :(

---

### Post by chazzjazz on 2005-11-09
hey i have 2 Gb RAM, having a 4Gb swap file is pretty slow isnt it???

espcially as it ries to delete it lol

i use a 200Mb swap in windows so that when out of swap it can quickly delete it and start a fresh

---

### Post by Vorian on 2005-11-09
[QUOTE=chazzjazz]are RAID working on linux??[/QUOTE]

YES:)

---

