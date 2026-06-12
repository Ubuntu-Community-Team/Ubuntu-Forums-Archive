---
title: "dual boot problem"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Coot2 on 2007-11-09
Ubuntu was loaded as dual boot opsys on laptop from CD. I'm trying to change boot.ini to make Windows default but boot.ini shows only 1partition, Ubuntu so I can't just swap order. Why are both partitions not shown and how do I make windows the default on boot?

---

### Post by amingv on 2007-11-09
Hello,

You won't find your Ubuntu partition in boot.ini under windows, because windows' bootloader can't/won't handle this partition. You need to log into Ubuntu and modify the grub.conf file.
Note that when you install Ubuntu booting is handled by GRUB and not by Windows anymore, because it can recognize both OSs.

---

### Post by natehatewindows on 2007-11-09
type this into a terminal
```
sudo gedit /boot/grub/menu.lst
```

the way i think you can do it (i dont because i want ubuntu default) is simply move the wondows before the ubuntu, you will see the entries below the 
## ##End Default Options ##

just make sure windows is the first one under this. there might be another way but this seems easiest to me.

so something LIKE this will be right under the ## ##end default options## (this is mine so you cant use it, your system might be different.

title		Windows Vista(loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by oilchangeguy on 2007-11-09
try this:
 How to add Windows entry into GRUB menu

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

    * Append the following lines at the end of file 

title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

    * Save the edited file

---

### Post by celticbhoy on 2007-11-09
At the start of your menu.lst file is a line like this :-

Default=0

The 0 points to the first entry in your grub list. So if you have a standard dual boot setup Ubuntu will be 0, Recovery will be 1, Memtext86 will be 2, A dividing line will be 3, and your windows boot will be 4.

if you change the above line to :-

Default=4

this should fix the problem, but check by counting the lines in your grub menu and subtracting 1 from the windows entry.

---

### Post by celticbhoy on 2007-11-09
You could also insta startup-manager from the repos, and this will give you full automated control over and changes you want to make to Grub

---

### Post by spideygal on 2007-11-09
title Microsoft Windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

My windows is on /dev/sda2 How would I add this? and would it stop me from booting windows or would there be an option.
  I am not familiar with rootnoverify

---

### Post by Duck2006 on 2007-11-09
Change this

title Microsoft Windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

to this

title Microsoft Windows
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

Windows sould still boot ok.

---

