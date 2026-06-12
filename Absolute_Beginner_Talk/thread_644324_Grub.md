---
title: "Grub"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by bachibusuc on 2007-12-18
Hi,

I'm about to re-install win xp on my c: drive(I have 80Gb(c: , d: ) + 320Gb(e:, f:)  and another one(40Gb) for linux), the thing is that, I installed grub on the windows partition(c:), and Im about to format this drive. I'm wondering first of all: If it's possible to install grub on another partition(i.e. the one for linux, i'm not formatting often linux partition so I wouldn't have to worry each time I format windows (which i format every month cuz of the viruses argg....))
So is it possible to install grub on another partition other than the one with windows?

second of all, im actually going to delete the grub from c: while formatting, do you know what's the command to install back grub? I think on fedora we have to reboot and go in text mode and put something chroot or something like that!

If anyone has time, help would be appreciated!! :)

---

### Post by Duck2006 on 2007-12-18
Grub would hve install a boot loader in the MBR of the first drive. When you install windoze it will over write the MBR and you will have to reinstall grub to be able to dual boot this may help with the reinstall of grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bachibusuc on 2007-12-21
thx man!

---

