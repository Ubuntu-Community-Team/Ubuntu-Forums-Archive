---
title: "Removing boot menu and kubuntu"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2007-05-05
Until recently I just had Ubuntu 7.04 on my home PC but I wanted to try Kubuntu so I installed it too and now have a dual boot system. Well know I've found I don't want/need it anymore. 

How do I get my system back to normal?

Thank you.

---

### Post by matburton on 2007-05-05
1. Remove the partition with the OS that you don't want any more.
I'd use gparted:
```

sudo apt-get install gparted
sudo gparted

```

WARNING: Be careful with this though, back-up everything important first!

2. Edit Grubs menu
```
sudo gedit /boot/grub/menu.lst
```

You want to remove the entry you don't want any more, something like this:

```

title		Kubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

Hope that helps ;)

---

### Post by FireFusion on 2007-05-05
Thanks for your reply matburton.

However the boot menu is coming from the Kubuntu install not my Ubuntu install. Is it safe to just get rid of Kubuntu and hope that removes it's boot menu too?

---

### Post by Pistolla on 2007-05-05
Didja use the "live CD," apt-get or aptitude? In either case, use the terminal (applications-accessories-terminal) and "sudo (either apt-get or aptitude) remove kubuntu desktop. 
Now if you used the "live CD" then i would assume it would be aptitude (to use to remove Kubuntu)

---

### Post by matburton on 2007-05-05
Ah I see what you mean.

In that case I'd look at this thread
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=24113[/COLOR]]("http://ubuntuforums.org/showthread.php?t=24113")

Basically you can use the live CD to reinstall grub and the live cd has gparted to remove the defunct partition.

Personally I'd use the second posted method ;)

Hope that's better!

---

