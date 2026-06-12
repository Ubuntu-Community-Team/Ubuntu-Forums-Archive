---
title: "can't read mkv file on mac os that were copied from ubuntu"
date: 2009-07-18
forum: Apple Hardware Users
---

### Post by silverwhalle on 2009-07-18
i mounted /dev/sda2 for mac os x on /media/mac. 
$sudo mount /dev/sda2 /media/mac
$mount -t hfsplus
/dev/sda2 on /media/mac type hfsplus (rw)
$cat /etc/fstab
...
/dev/sda2    /media/mac    hfsplus    rw,user,noauto    0    2
------------------------------------------------------------------
and copied some videos into /media/mac. and rebooted into mac osx leopard.
i have mplayer for mac and binary codec packages installed on mac os.
but mplayer couldn't open **.mkv file encoded with x264 that were copied from ubuntu. why? but i could open normal text file created from on ubuntu.

right.. i can play it on ubuntu. but there's some problem with cpu usage when playing videos on ubuntu that i would like to question about later. so for the time being, i want to play those high quality videos on mac. 

how can i open those file on mac?

---

