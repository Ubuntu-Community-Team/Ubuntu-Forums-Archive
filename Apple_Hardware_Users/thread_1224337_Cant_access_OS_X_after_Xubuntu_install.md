---
title: "Cant access OS X after Xubuntu install"
date: 2009-07-27
forum: Apple Hardware Users
---

### Post by ianMac1 on 2009-07-27
I have an iBook G4 (PPC). I used Gparted from the Live CD to partition the drive, installed Xubuntu and now I cant access OS X. When I use Gparted in Xubuntu to see the HD it says it cant mount the Macintosh drive because it's locked. Any suggestions?? I really wanted to set it up as dual boot... this is my first experience using Ubuntu so I'm a noob when it comes to using the terminal so any help would be greatly appreciated.

---

### Post by stockley on 2009-07-28
Try installing rEFIt
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Not sure if it will help, but it might :P

---

### Post by dewy666 on 2009-07-28
have you tried booting holding the option key
also try to boot off the OS X install disk and run disk utility and repair the disk

---

### Post by rjcalifornia on 2009-07-28
Same thing happened to me....

What I did was reinstalling OSX, but you have to use the partition manager from the OSX CD Installer. However, you have to format the Linux Partition as free space. 

Hope that helps!

---

### Post by Tofuik on 2009-07-28
I think I remember hearing somewhere that if you use Gparted to do the partioning it messes up the OSX installation.  I had leopard so I did mine with bootcamp.

---

### Post by ianMac1 on 2009-07-28
> **Tofuik said:**
> I think I remember hearing somewhere that if you use Gparted to do the partioning it messes up the OSX installation.  I had leopard so I did mine with bootcamp.
Thanks for the help guys.  Wish I would have known that earlier lol

---

### Post by dewy666 on 2009-07-29
so which way worked for you then

when i put ubuntu onto my mac i decided to increase the ubuntu partition and decrease the osx partition and the only way for me to do that was with a gparted live disc so afterwards my drives were playing up so after 2 hours of trying to figure it out i used my leopard install disc to boot and use disc utility to find and repair problems to both discs without losing data on either

---

### Post by W4l0ck on 2009-07-29
I hade a similar problem.

---

