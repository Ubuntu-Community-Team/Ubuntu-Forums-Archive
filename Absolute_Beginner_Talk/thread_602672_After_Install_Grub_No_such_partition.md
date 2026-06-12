---
title: "After Install: Grub: No such partition?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by fizz on 2007-11-04
I'm having a hard time for some reason getting grub to work properly. This is a new gutsy install.

Some basics: Im using the 64 bit install
I have two hard disks.

hd0 which is just some NTFS partitions and hd1 (sda) which is my windows install and on sda6 (hd1,5) my linux install

When it boots, grub shows and i hit enter and get the message above. So i go to grub command line,
do find /boot/grub/stage1 it finds it on hd0,5

so i change it to
root (hd0,5)
setup (hd0) but still get the same thing.

I have no idea why its being like this, its reallllly annoying though.

---

### Post by fizz on 2007-11-04
bump

---

### Post by fizz on 2007-11-04
Alright, I figured things out. Now it would be nice if I didn't need to use nosplace and remove quiet from the boot line...

---

### Post by Can+~ on 2007-11-04
You can edit /boot/grub/menu.lst for all those settings, or download Boot-Up manager.

---

