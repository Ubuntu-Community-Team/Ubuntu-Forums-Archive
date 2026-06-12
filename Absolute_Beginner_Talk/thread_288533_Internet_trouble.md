---
title: "Internet trouble"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by cactaur on 2006-10-30
Ok, this is basically a remake of [my previous thread]("http://www.ubuntuforums.org/showthread.php?t=287642"), but I moved it and have more updated information.

Ok, so, I had a recent incident with my computer, which ended up with me changing the permissions of my entire filesystem to drwxr-xr-x root:root (Except for /tmp and /home). So, basically, before this happened, I had internet. Now, when I use my computer or the Dapper live cd, I can't use the internet. When I use my laptop (which has breezy), I can use it. On Networking, it can detect my network, but when I connect, it takes forever to activate ath0. Then when it does, there's still no connection.

---

### Post by dmizer on 2006-10-30
if you changed permissions at a global level, your best bet is simply to reinstall.  the wide and varied permissions are neccessary to the function of linux, and frankly, i'm surprised your box is working at all.

edit: i believe the reason things could be having problem on the live cd is possibly due to a permissions change on your swap partition, as the live cd will make use of the swap partition on your hard drive.

you can try a "noswap" boot option on the live cd to test this theory.

---

### Post by cactaur on 2006-10-30
Oh, I didn't touch my swap partition, it's only my Ubuntu partition. And actually, it took two weeks of work to get my box to function after that. GNOME went berzerk because the /tmp had specific permissions.

And the thing with the Live CD, when I don't specify a network, the internet works. When I try to have it connect to my network, it doesn't. I'm sure I put the WEP key in right.

---

