---
title: "ubuntu won't load"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by EddieFudd on 2006-09-09
i have 3 hard drives in total, 1 has xp on and the other has ubuntu just installed. i think this might be my problem? as when i boot i get the windows boot manager with lets me choose xp or vista. i then changed it so the hd with ubuntu was booted first but it doesn't load still, help please ](*,)

---

### Post by jorn on 2006-09-09
Does "grub" the bootloader appear when you boot the ubuntu hd? press the"escape"key when you see "lading grub" or something on the boottom of the screen.

---

### Post by EddieFudd on 2006-09-09
no nothing to do with ubuntu loads when i use that hd as my first boot drive

---

### Post by EddieFudd on 2006-09-09
anyone with some ideas?

---

### Post by jorn on 2006-09-10
At the end of a Ubuntu- istallation the installer looks for other operating sytems on your harddrives and will add theese to "grub" the bootloader which is then installed by default on the MBR (Master Boot Record)on your first harddrive.
Have you changed the order of your drives or added any drives after installing Ubuntu? If that is the case you can get grub on the MBR :
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28mbr%29%7C%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28mbr%29%7C%28grub%29)
There are other possibilities. Try a search.

---

