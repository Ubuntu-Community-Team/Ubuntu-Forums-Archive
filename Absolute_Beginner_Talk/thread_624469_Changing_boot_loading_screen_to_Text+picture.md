---
title: "Changing boot loading screen to Text+picture"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Tango_Down on 2007-11-27
So, I am running Gusty and was just curious if I can use boot screens (The progress screen while ubuntu is loading) downloaded from kde-look. I am currently using KDE, and changed to KDM from GDM. Looking about it seems that Ubuntu uses USplash, which I don't think I can use the theme I downloaded with. Really all I want is the text startup with a background picture rather than the fairly meaningless progress bar. Thanks in advance for any help provided.

---

### Post by Aniongap on 2007-11-27
Hi,

you can try to copy downloaded splash.xpm.gz to boot/grub

then 

sudo update-grub

p.s. dont forget to enable in boot.conf splash screen

---

### Post by Tango_Down on 2007-11-27
The archive is tar.gz, and furthermore the pictures and config files are .jpeg and .cfg files, so I don't think that will work. I suppose I would have to manually change the bootsplash pictures and whatnot, as well as the config file.

---

