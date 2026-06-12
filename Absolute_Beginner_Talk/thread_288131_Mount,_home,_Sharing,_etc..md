---
title: "Mount, /home, Sharing, etc."
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-10-29
I keep seeing these words in many tutorials while trying to understand how I can share some files between XP and Ubuntu. I already have Dapper running, which is my first Linux distro, and I safely chose to install it on a separate drive.  I'm planning to do a fresh install of Edgy, and this time I want access to some files in XP from Ubuntu. As I said, I keep seeing those words, but I understand none of it. Can some explain them or link to websites which explain them to newbies?

Currently, the second hard drive is made up of Ubuntu and a Windows partition, that's sitting there doing nothing. So, I can wipe it off completely before installing Edgy.

P.S. I'm downloading the alternate installer and have GParted for partitioning.

---

### Post by taurus on 2006-10-29
Best way is to create an empty partition and call it /share.  Format it as fat32/vfat so you can write and read to it from both Edgy and Windows.  Here is more info about mounting and what not.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by CatKiller on 2006-10-29
> **navneeth said:**
> As I said, I keep seeing those words, but I understand none of it. Can some explain them or link to websites which explain them to newbies?

[mount]("http://en.wikipedia.org/wiki/Mount_%28computing%29")
[/home]("http://en.wikipedia.org/wiki//home")
["Sharing is the joint use of a resource..."]("http://en.wikipedia.org/wiki/Sharing")

---

### Post by navneeth on 2006-10-29
> **taurus said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

That's one of the pages I went to, but I'm not able to understand even the first few lines. Could you please tell me what the following means?

> If you already have your Windows partitions mounted (but with the wrong permissions), unmount them before beginning these instructions. For example, if your Windows partition is mounted as /media/hda1, then open up a terminal and type
sudo umount /media/hda1

Thanks.

---

### Post by navneeth on 2006-10-29
> **CatKiller said:**
> [mount]("http://en.wikipedia.org/wiki/Mount_%28computing%29")
[/home]("http://en.wikipedia.org/wiki//home")
["Sharing is the joint use of a resource..."]("http://en.wikipedia.org/wiki/Sharing")

Thanks :). Wiki is one of the first places I go to, but I'm not looking only for definitions and such, but something that is more practical, and aimed towards the beginner. You may well say that Asiyu's site is just the place for me, but certain things still tend to go over my head.

---

### Post by CatKiller on 2006-10-29
> **navneeth said:**
> You may well say that Asiyu's site is just the place for me, but certain things still tend to go over my head.

Actually, I've felt that some of the psychocats tutorials could do with a bit more explicative info. Sometimes it's easier to get some definitions, and some instructions to get the end point, and then just do some mental gymnastics to get between the two, rather than hoping for someone else to have documented the process. It helps that I've got a friend to talk to who's already done a lot of the intermediate steps and can't tell me if I'm just being stupid, though ;)

---

### Post by navneeth on 2006-10-29
> **CatKiller said:**
>  It helps that I've got a friend to talk to who's already done a lot of the intermediate steps 

Since I don't have one, I come here. ;)

---

