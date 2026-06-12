---
title: "ubuntu refuses to load graphics"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by binzer on 2007-11-09
Hi,
Ubuntu fails  while booting. It never goes beyond "etc/rc.local"   and can't see  the login screen. I suspect that the problem is failure to boot the graphics. I manage to get a command line using "Ctrl"+ "Alt" + "F7", but rebooting using the commands "startx" or "sudo dpkg - reconfigure xserver -xorg" + "sudo /etc/init.d/ gdm restart" are helpless.
any idea plz?
Thanks in advance!

---

### Post by Pumalite on 2007-11-09
Is this failure to boot a Live CD or failure to boot a system just installed from the hard drive?

---

### Post by binzer on 2007-11-09
Sorry for not  being clearer. I've installed Ubuntu in my Pc. So It is the OS  in the pc drive which fails to boot.
regards,

---

### Post by Pumalite on 2007-11-09
If you can boot a Live CD, post from Terminal:

sudo fdisk -lu
cat /boot/grub/menu.lst (after mounting partition)

---

