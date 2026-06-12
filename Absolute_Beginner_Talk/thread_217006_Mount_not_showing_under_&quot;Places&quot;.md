---
title: "Mount not showing under &quot;Places&quot;"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-07-16
I setup my system to auto mount some ntfs drives and that seems to work ok. I can access them from  /mnt/ntfs1 and /mnt/ntfs2.

However these drives are not quickly accessible from "Places" How can I get them to show up there?

---

### Post by bluecherry on 2006-07-16
I don't know if this will help but i've had a similar issue when mounting my ipod.

***-- You probably did this already --***
First I created a dir /media/ipod with "sudo mkdir /media/ipod".

Then I added the entry for my ipod in the fstab file:
/etc/fstab entry:
> 
/dev/sda    /media/ipod    vfat    sync,user,noauto,umask=000    0 0


The device now shows up in Places > Computer

***-- This is what you're looking for --***

Assuming you are mounting the device to /media/ntfs1 this will work:
> 
ln --symbolic /media/ntfs1 ~/ntfs1


-> you've created a link to the device named ntfs1 in your home directory. 

In nautilus, drag the folder (link) ntfs1 to the left side (where you're places show up). Once it's there it will also show up in your "Places" menu.

Hope this helped.

grtz

---

### Post by toykilla on 2006-07-16
Thanks. That worked.

---

