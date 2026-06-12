---
title: "Installing Lilo/grub"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by kane77 on 2006-10-09
Hi, I installed ubuntu from the ship it cd (or is it a dvd?) and the installation process went OK. I installed it to 2nd partition of 2nd disk. (just to include all the details: 1st disk is sata disk and 2nd is ATA).
BUT the installation did not install neither Lilo nor Grub so now I believe it is installed but I have no choice to boot into it. It runs normally windows.
How can I fix it??

---

### Post by bulldog on 2006-10-09
You can reinstal grub from the live cd and put it on your Ubuntu hdd.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

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

### Post by Kateikyoushi on 2006-10-09
Try to change the BIOS setting to boot from the other drive.
Most likely grub has been installed there.

---

### Post by kane77 on 2006-10-09
will this leave windows accessible (i'm curious because when I installed ubuntu a while ago it made windows not boot)

---

### Post by bulldog on 2006-10-09
> **kane77 said:**
> will this leave windows accessible (i'm curious because when I installed ubuntu a while ago it made windows not boot)

Yes and if it's not automaticly put in your menu.lst it's simple to add it.

Is windows on the other hdd?

If yes set BIOS toboot from the Ubuntu hdd and install GRUB there.
Add your windows boot at the menu.lst and let the windows hdd as it is.

So you can start windows via GRUB and if this fails for some reason you can start windows by changing the boot device into the windows hdd.

---

### Post by kane77 on 2006-10-09
thanx I did the latter (switched the boot priority to second disk) and it actualy works so thank you!

---

