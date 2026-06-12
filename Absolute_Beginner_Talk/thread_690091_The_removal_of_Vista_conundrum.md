---
title: "The removal of Vista conundrum"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2008-02-07
Hey Guys,

I want to remove vista, however i have no idea of the process of removing the vista partition and the configuring grub to remove vista as a boot-up option.

Can anybody help?

Thanks,
Kristian

---

### Post by appleimac on 2008-02-07
Hi there I think when you goto install Ubuntu it says do you want to remove all partitions on this system just click that and bingo vista is gone for good :D

---

### Post by jan quark on 2008-02-07
you can download the gparted live CD and boot from it and format the vista partition

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Rocket2DMn on 2008-02-07
You can also use your Ubuntu LiveCD and go to System->Administration->Partition Editor
Both get you to the same thing essentially.  Once there you can delete the vista partition and either resize your root partition to cover the empty space or you can format it and use it as a data partition.  
If you select to resize, please make sure you have your important files/data backed up because you never know when you fiddle with partitions... (shouldn't be a problem, but I would feel bad without posting the warning).

You can then remove the Vista entry from GRUB:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```

---

