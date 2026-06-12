---
title: "google earth on edgy"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-24
the googleearth website only supports up to 5.10
does anyone know how to make it work for 6.10?

here is a pic of wat it looks lik (this is supposedly a pic of new york, new york)

[IMG]http://i130.photobucket.com/albums/p270/cardmaster91/googearth.png[/IMG]

---

### Post by fatneck on 2006-11-24
I have Edgy 6.10 i386 and it runs fine on mine. I used Automatix2 to get it though, worked a treat!

---

### Post by Cardmaster91 on 2006-11-24
wats automatix? is that a windows emulator, like wine?

---

### Post by fatneck on 2006-11-24
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Cardmaster91 on 2006-11-24
thx

---

### Post by Cardmaster91 on 2006-11-24
ok, i used automatix to get goog earth, nut it still doesnt work. its all wierd just like before

---

### Post by taurus on 2006-11-24
What's your graphic card and have you installed a driver for it?

---

### Post by turbojugend_gr on 2006-11-24
IT's not the automatix that made things work, it's most propably you not having set up your graphic card's drivers.

EDIT: DIdn't see your post taurus, so I second that I guess would be enough ;).

---

### Post by Cardmaster91 on 2006-11-24
> **taurus said:**
> What's your graphic card and have you installed a driver for it?

i have nvidia 6100, and ive installed it.  ...

umm i dont remember how, but automatix said that it was already installed.

---

### Post by mseeba on 2006-11-28
I have the exact same problem on Dapper. I have a Dell XPS M1210 with NVidia graphics and the NVidia kernel driver loaded and working.... 

Would love to find a solution as  it is a very cool program.

---

### Post by ramjet_1953 on 2006-11-28
Same problem here using an Acer TravelMate 4100, with Intel grapics chipset and 915resolution driver.

Roger :-k

---

### Post by Cardmaster91 on 2006-11-28
yep ive even tried reinstalling ubuntu (i had to anyways), but it still doesnt work. i installed ubuntu, got automatix, installed almost everything, but goog erth dont work

---

### Post by ORF1000 on 2007-01-26
Same problem here with an nvidia Geforce 6200.  Works fine if I boot the box into WinXP, but not in Linux.  Everyone reporting trouble with Google Earth seems to be running an nvidia card.

---

### Post by Cardmaster91 on 2007-02-14
i'm back again. and although i never did get it to work, i now have a different problem. I'm using an entirely different computer now. I put ubuntu on, got automatix, installed it, and when i run it, it says to download drivers for my graphics card. I click continue, and the earth isn't there. so i want to dl drivers, but i haven't the faintest idea what kind of graphics my computer has, and i wouldn't know how to install the driver in ubuntu, can anybody help me?

---

### Post by sebbouckaert on 2007-02-22
The video issue with Google Earth described here seems a common problem with nvidia graphic cards and the drivers from the ubuntu repositories and/or automatix. 
I used to have exactly the same problems after installing/uninstalling the nvidia several times driver through automatix and also the adept install manager (I'm using Kubuntu). 

After some google research I found this [http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/635301/page/vc/vc/1](http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/635301/page/vc/vc/1)
So i've updated my nvidia driver from here [http://www.nvidia.com/object/unix.htm](http://www.nvidia.com/object/unix.htm) to version 9631
and now my planet renders smoothly :-)

hope this helps

---

### Post by aktiwers on 2007-02-22
Find out what card you have! Maybe you can use the nVidia/ATI install script.

---

