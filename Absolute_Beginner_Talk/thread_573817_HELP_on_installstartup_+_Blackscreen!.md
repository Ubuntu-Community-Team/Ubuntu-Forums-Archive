---
title: "HELP on install/startup + Blackscreen!"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by chraej on 2007-10-12
I'm currently trying to dual boot 7.04 to install correctly on my HP dv6125 laptop (1 gig Ram,Nvida GeForce 6150 GO gfx, 120 gig hdd) with XP and i'm running into alot of problems.

first of all i've gotten 7.04 dual booted about a week ago with mixed results and tried to change my resolution which messed up my settings so i couldnt see the screen at all and so i decided to format and just reinstall since it had only been about a day since original instal...

however since then i've not been able to get a stable re install working whatsoever.

i've formated the partitioned space for linux with both windows and the linux cd so there should be no traces whatsoever from previous installs

i've tried to reinstall about 10 times using 3 different cd's of x64 7.04 and gotten bad results

my current problem: I install linux on 2 primary partitions, Swap(.5 gigs) and Root(10 gigs) and i get through the install process.

i reboot my computer as i am asked to do after complete install, Grub boot loader works fine, all my OS's are accounted for, i boot into Ubuntu

**The Orange load screen freezes on 3 bars ALOT  OR  the load completes and the entire screen just goes BLACK**

(when frozen on 3 bars the error i get is that i am out of buffer space??)
anyone know how to fix this?!

---

### Post by Bliepo32 on 2007-10-12
I have been expierencing similair problems with my version, but luckily, I also found a fix. See [Ubuntu not booting normally]("http://ubuntuforums.org/showthread.php?t=572074").

---

### Post by chraej on 2007-10-12
how do you disable the splash screen?

---

### Post by Bliepo32 on 2007-10-12
Ow. Sorry, I forget to tell you. Read [Disable splash screen?]("http://ubuntuforums.org/showthread.php?t=542082&highlight=disable+splash+screen") And be sure to make a back-up first with:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

If you screw things up, you can restore it with:
```
sudo mv /boot/grub/menu.lst.backup /boot/grub/menu.lst
```

---

### Post by chraej on 2007-10-12
can i do this from the grub console line? b/c i cant currently get into ubuntu even through recovery

when trying to use recovery i got these errors:
> 
...
setting up console font and keymap... 
 then it froze there
> 
...
loading hardware drivers...
error recieving uevent message: No Buffer Space available


and frozen

---

### Post by Bliepo32 on 2007-10-12
No, you cannot do this from GRUB. You could use you cd for it though.

---

### Post by chraej on 2007-10-12
yeah, i can use the cd's recovery to get into the command line and even into some form of ubuntu itself if i type startx.

how exactly do i remove the splash/quiet from the terminl/command line?

---

