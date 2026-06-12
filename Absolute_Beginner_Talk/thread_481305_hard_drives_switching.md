---
title: "hard drives switching"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by bapho on 2007-06-22
heya all
just a bit of a problem with my hard drives
the one im using to dual boot feisty fawn and XP is a seagate 180gb and my storage drive is a samsung 400gb 
the problem is whenever i have both hard drives in, my storage drive always becomes /dev/sda1 by default and my boot drive becomes /dev/sdb1 (xp) and /dev/sdb2 (ubuntu), /dev/sdb3 (/home) and  /dev/sdb4 (swap)
is there any way to switch it back? cause feisty is failing to load my swap partition now =(

---

### Post by phr0ze on 2007-06-22
Try switching the ports the drives are plugged into.

---

### Post by Inxsible on 2007-06-22
Are you saying that when your Samsung storage drive is NOT connected, your Seagate is /dev/sd[COLOR=red]a[/COLOR] ?

---

### Post by bapho on 2007-06-22
thanks for the quick reply guys ^^
i tried switching the ports which they are connected to on the motherboard but no luck =(
the boot drive (seagate) is /dev/sda when the samsung storage drive is unplugged
as soon as i plug in my storage drive and boot to ubuntu it automatically takes the /dev/sda mount point and the boot drive ends up as /dev/sdb
im not sure if thats the reason why ubuntu is failing to load swap but i'd imagine that would be the root of the problem

---

### Post by bapho on 2007-06-22
sorry inxsible i didnt read your post properly
but yeah thats exactly right

---

