---
title: "Macbook, Bootcamp, and ubuntu!"
date: 2007-05-28
forum: Apple Intel Users
---

### Post by kingfoot on 2007-05-28
So, I'm going for the ultimate machine. haha. not really, but this is just an experiment. So, I have a macbook (2.0 ghz with 2gb of ram, 80gb hdd, and the workings.) so ive got a good machine. ive already got windows xp sp2 up and running on it (18gb partition using bootcamp) and ive got about 10gb left in the windows part. (20gb free in the mac part). so i'm just wondering, instead of partitioning again on the mac side, could i use wubi on the windows side? i dont see why not... also, with wubi, can i use any distro iso i want? cause i have the ultimate edition downloaded already, or should i start fresh with the newest ubuntu? thanks everyone in advanced!

---

### Post by Gen2ly on 2007-05-28
> **kingfoot said:**
> So, I'm going for the ultimate machine. haha. not really, but this is just an experiment. So, I have a macbook (2.0 ghz with 2gb of ram, 80gb hdd, and the workings.) so ive got a good machine. ive already got windows xp sp2 up and running on it (18gb partition using bootcamp) and ive got about 10gb left in the windows part. (20gb free in the mac part). so i'm just wondering, instead of partitioning again on the mac side, could i use wubi on the windows side? i dont see why not... also, with wubi, can i use any distro iso i want? cause i have the ultimate edition downloaded already, or should i start fresh with the newest ubuntu? thanks everyone in advanced!

Its a just cause kingfoot but...  Apple created a unique partitioning scheme when it decided to allow other OS's to boot alongside OS X.  It's a EFI/GPT/MBR hybrid, and I haven't heard anyone successfully resizing and therefor adding a new one.  You will probably (for best success) have to start from the beginning once more, including reinstalling OS X!  Take a look at the [Gentoo Guide]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook") as it has a nice section on how to do this.

---

### Post by ronocdh on 2007-05-29
> **Dirk.R.Gently said:**
> Its a just cause kingfoot but...  Apple created a unique partitioning scheme when it decided to allow other OS's to boot alongside OS X.  It's a EFI/GPT/MBR hybrid, and I haven't heard anyone successfully resizing and therefor adding a new one.  You will probably (for best success) have to start from the beginning once more, including reinstalling OS X!  Take a look at the [Gentoo Guide]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook") as it has a nice section on how to do this.
I second that you start over. However, if you're interested in easing into Ubuntu (as your mention of Wubi suggests), you could try VMWare Fusion beta3 on OS X and run Ubuntu in virtualization like that. Not quite the same, but at least you'll know the ropes before diving in and having to configure wireless (if you have Core2 Duo), etc. Just a thought, post back with what you decide to do!

---

### Post by AWerner32 on 2007-05-29
I'm not the expert here but it seems to me you could shrink the windows partition with gparted and install it there if you could do the install right, and then also install refit. Make sure you inly install grub on the linux partition and i think that would work, at least i dont see why not.

---

### Post by josephmclaughlin on 2008-05-28
The Wubi install works fine on an XP boot camp partition. I have step by step instructions on how to do it here: [http://blog.josephmclaughlin.info/](http://blog.josephmclaughlin.info/)

Hope this helps,

Joseph McLaughlin

---

