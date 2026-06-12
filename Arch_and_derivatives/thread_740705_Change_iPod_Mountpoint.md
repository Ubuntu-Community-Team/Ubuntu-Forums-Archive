---
title: "Change iPod Mountpoint"
date: 2008-03-31
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-03-31
Arch mounts my iPod (30 GB 5th generation) to /media/<my ipod name> . The name on my iPod is Keerthi's iPod and when it is automounted it ends up in a weird **/media/KEERTHI'S** folder... LOL! 

How do I change it to automount to **/media/iPod**. I refered to the [wiki]("http://wiki.archlinux.org/index.php/HAL#Policies") and learnt about policy files. But I'm afraid I can write a **/etc/hal/fdi/policy/preferences.fdi** file as the wiki mentions that it is deprecated from hal => 0.5.10. 

So what is the suggested way to change iPod mount point?

---

### Post by kpkeerthi on 2008-04-28
SOLVED.

Just in case if anyone is in need, here are the steps:
1. Get & confirm the current volume label:
```
sudo mlabel -i /dev/sdb2 -s ::
```
2. Set the new volume label (as iPod)
```
sudo mlabel -i /dev/sdb2 -s ::iPod
```

My iPod now auto mounts to /media/iPod

---

### Post by SteveGodfrey on 2008-07-16
Thanks for the instructions.

I had to install mtools which gives you mlabel.
I had to create a .mtoolsrc in your home directory and add the following line mtools_skip_check=1
The syntax is wrong for renaming the iPod. You've specified '-s' which only shows the current name, use '-n' to actually rename.

so I used 

sudo mlabel -i /dev/sdb2 -n ::iPod

---

### Post by Barrucadu on 2008-07-16
I'd never heard of mlabel - I'll have to label some things, thanks.

---

