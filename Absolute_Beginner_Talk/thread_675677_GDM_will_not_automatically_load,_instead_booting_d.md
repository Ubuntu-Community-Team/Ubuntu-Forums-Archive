---
title: "GDM will not automatically load, instead booting directly to CLI"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by OSlinuX on 2008-01-22
Im currently using Dapper and yesterday there was an update. The update required me to restart. Eventually i did restart, but now its booting directly into the CLI.
I can start gdm by typing
[PHP]startx[/PHP]
or
[PHP]sudo /etc/init.d/gdm restart[/PHP]
If i run startx, i get an error stating "Warning, Power Manager, The program cannot start until you start the dbus system service"
If i run sudo /etc/init.d/gdm restart I get the before mentioned error and a "Failed to initialize HAL" error
Since all the problems started at the same time, they may be all have the same root.
Does anyone know how i can boot into Ubuntu and have the gdm boot automatically?

Thanks in advance

---

### Post by meborc on 2008-01-23
you might have a partial upgrade... try to upgrade again, or to see if package "ubuntu-desktop" is installed

---

### Post by OSlinuX on 2008-01-23
unfortuantely the above did not fix the problem. what script is it that calls gdm?
that file may be corrupt

---

### Post by bwtranch on 2008-01-23
Try installing at least Feisty (7.04). Don't try an upgrade from Dapper. Use a fresh install (i.e. live cd, if possible). A lot has changed since Dapper.

---

### Post by OSlinuX on 2008-01-23
So i start thinking about how it may be that the run level is set wrong in /etc/inittab, so i change it from 5 to 2 and it still boots to the CLI. 
Than i think... according to all the stuff i read, only runlevel 3 should be booting to CLI.
Maybe its that im not booting to the correct instance of Ubuntu, i see what it is im booting to, and it turns out ive been booting to recovery mode the entire time.
My /boot/grub/menu.lst is by default set to boot to option 1, which was at one point normal Ubuntu mode. 
Somehow my menu.lst was edited, the first entry (0) was Windows, it had completely disappeared!
So i had by default been booting to Ubuntu recovery mode.

Its very odd, could the last update i downloaded have edited my menu.lst ?

either way, I added my windows entry back to the menu.lst file, told it to boot by default to Ubuntu normal mode and all is well again.

---

