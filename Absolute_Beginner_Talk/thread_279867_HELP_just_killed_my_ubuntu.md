---
title: "HELP just killed my ubuntu"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by pregoeater on 2006-10-18
i edit the grub menu to change a splash screen now it loads up says splash screen not found and just reboots over and over help please.



thanks pre

---

### Post by elchinovi on 2006-10-18
If you have a Live CD, boot from it, and go to /boot/grub/menu.lst and undo any changes that you've made or load the menu.lst backup.
Hope that works!
Good Luck!

---

### Post by pregoeater on 2006-10-18
cant wont let me in the drive from the cd

---

### Post by bulldog on 2006-10-18
Turn the computer off.

Then on again and set in BIOS to boot from cd.

If you enter the desktop mount your install by typing in your terminal```
sudo mkdir /mnt/rescue
```
Then mount your install,you have to know where your ubuntu is installed.

If you don't know type ```
sudo fdisk -l
``` l as in like,to see where your root partition is.

Then mount it by typing```
sudo mount /dev/??? /mnt/rescue
```
[??? stands for your root partition]

Then to open your menu.lst```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```and alter it back as it was.

---

### Post by elchinovi on 2006-10-18
Have you tried changing the boot sequence?

Bulldog just killed me!
](*,) 
I could not have said it better
:mrgreen:

---

### Post by Crooksey on 2006-10-18
from the live cd

```


sudo mkdir /mnt/linux/ubuntu
sudo mount /dev/hda2 /mnt/linux/ubuntu (assuming /dev/hda2 is your ubutnu /)
cd /mnt/linux/ubuntu/boot/grub
sudo nano menu.lst


```

---

### Post by pregoeater on 2006-10-18
same error even after i change it back

---

### Post by bulldog on 2006-10-18
Reinstall GRUB with the live cd.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by pregoeater on 2006-10-18
tried both things...still get error says failed to read splash image ((hd1,0)/boot/grub/blu.xpm.gz) then just reboots over and over.

---

### Post by bulldog on 2006-10-18
Well remove the /boot/grub/blu.xpm.gz then if it makes the trouble.

Do this first and the reinstall GRUB.

If I'm correct it should be in /boot/grub/images/blu.xpm.gz

---

### Post by pregoeater on 2006-10-18
i cant delete wont let me

---

### Post by pregoeater on 2006-10-18
deleted the file still does same thing??? i dont understaND

---

### Post by bulldog on 2006-10-18
```
sudo rm /mnt/rescue/boot/grub/blu.xpm.gz
```

I presume you still on the live cd and mounted your partition.

---

### Post by pregoeater on 2006-10-18
file is gone i get the same error...

---

### Post by bulldog on 2006-10-18
> **pregoeater said:**
> deleted the file still does same thing??? i dont understaND
 That's because grub looks for it.

Now reinstall grub.

---

### Post by pregoeater on 2006-10-18
same problem i deleted the file and reinstalled grub no change still get same error

---

### Post by pregoeater on 2006-10-18
i got it i had to edit the file again for some reason it got copied to to top off the file thank you so much for all your help. sorry if i was in a panic


thanks again
pre

---

### Post by picpak on 2006-10-18
Just for future reference, you can automatically update your GRUB config with

```
sudo update-grub
```.

---

