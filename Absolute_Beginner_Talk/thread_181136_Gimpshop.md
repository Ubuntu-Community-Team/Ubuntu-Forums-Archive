---
title: "Gimpshop ?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by arsenic23 on 2006-05-23
What's the best way to install Gimpshop on Dapper?   A link I can wget a .deb from would be awsome, but sensible instructions, or a link to sensible instructions would do.

---

### Post by tribaal on 2006-05-23
Thanks a lot for pointing this out, I've always been kind of turned down in front of the gimp, because of it's menu and windows structure... 
I'll make sure to investigate on how to best install it on Dapper :)

Thanks again for [the tip]("http://plasticbugs.com/?page_id=294") ;)

- trib'

---

### Post by aysiu on 2006-05-23
[This](http://ubuntuforums.org/showthread.php?t=67525) may help.

---

### Post by skippy81 on 2006-05-23
I would also love to find a *.deb file for it, maybe it will get added to the ubuntu repositories at some point - it would be good for users migrating from MS. 

On the downside, to my knowledge gimpshop doesnt alter the split window structure.  Apparantly having everything on one window is peculiar to Windows Photoshop, the Mac version I used at work had split panels just like the Gimp.  

Having all the menu items in the 'right' places would be great though, I decided to "Bring out the gimp" a couple of days ago and found the filters to be really good.

---

### Post by tribaal on 2006-05-23
Asyiu, just *how* in hell are you so fast and efficient when answering people's concerns on so many different topics? ;)

That's not even human! Are you an AI? ;)

Thanks a load for the link :)

- trib'

---

### Post by aysiu on 2006-05-23
[QUOTE=tribaal]Asyiu, just *how* in hell are you so fast and efficient when answering people's concerns on so many different topics? ;)

That's not even human! Are you an AI? ;)

Thanks a load for the link :)

- trib'[/QUOTE] I can't be AI... I've got to be a human being; otherwise, how could I be using Ubuntu? It's Linux... for human beings...

Well, it'll just be our little secret, I guess.

---

### Post by Clay85 on 2006-05-23
I found photoshop to be very confusing and anti-logic based. I latched onto GIMP from my WINXP machine very quickly and I haven't let go. What is Gimpshop?

I looked at [the link]("http://plasticbugs.com/?page_id=294"), it looks like GIMP for Mac. Is that correct?

---

### Post by aysiu on 2006-05-23
[QUOTE=Clay85]I found photoshop to be very confusing and anti-logic based. I latched onto GIMP from my WINXP machine very quickly and I haven't let go. What is Gimpshop?

I looked at [the link]("http://plasticbugs.com/?page_id=294"), it looks like GIMP for Mac. Is that correct?[/QUOTE] It's just a different interface, but it's still GIMP.

GIMP for Mac actually exists separately from GIMPshop, though they do make a version of GIMPshop for Mac as well.

---

### Post by flyingsolo on 2006-05-23
I've only ever had time to dabble in Photoshop elements, a demo of Photoshop 7 and a bit in the Gimp.  The Gimp seems very similar to PS but which version of PS would be most similar?  Anyone have links to discussion of relative merits of PS v. Gimp (beyond the obvious money issue!)?
Thanks

---

### Post by aysiu on 2006-05-23
Basically, the major difference that I've heard of is Photoshop having CMYK abilities that GIMP doesn't have. My wife showed me the difference, but I don't fully understand it. It has something to do with additive and subtractive colors and printing quality.

---

### Post by aysiu on 2006-05-23
Try pasting these three commands into the terminal: ```
wget -c http://web.njit.edu/~st7/mirror/GIMPShop/gimp_2.2.4-2_i386.deb
sudo dpkg -i gimp_2.2.4-2_i386.deb
rm gimp_2.2.4-2_i386.deb
```

---

### Post by javierfh on 2006-06-12
[QUOTE=aysiu]Try pasting these three commands into the terminal: ```
wget -c http://web.njit.edu/~st7/mirror/GIMPShop/gimp_2.2.4-2_i386.deb
sudo dpkg -i gimp_2.2.4-2_i386.deb
rm gimp_2.2.4-2_i386.deb
```[/QUOTE]


Hello, 

do you know if these lines are still working? 
I have tried to paste them into the terminal and i get the following errors.

sudo dpkg -i gimp_2.2.4-2_i386.deb
dpkg: error processing gimp_2.2.4-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gimp_2.2.4-2_i386.deb


Any clue what is wrong there? Im absolutely newby.

Javi

---

### Post by Enigmatic on 2006-06-15
I tried installing Gimpshop from the .deb (last link has been superceded), and I get this error:

dpkg: error processing gimpshop-2.2.11.deb (--install): trying to overwrite /etc/gimp/2.0/gimprc which is also in package gimp-data.

I tried the source file, but it said I needed GTK+, which I tried to configure but got this error:

checking for X... no
configure: error: X development libraries not found



What dependency do I need to satisfy it?

---

### Post by Kure on 2006-06-17
use this address (paste into browser) [http://web.njit.edu/~st7/mirror/GIMPShop/gimpshop-2.2.11.deb](http://web.njit.edu/~st7/mirror/GIMPShop/gimpshop-2.2.11.deb)

or paste into terminal:

```

wget -c http://web.njit.edu/~st7/mirror/GIMPShop/gimpshop-2.2.11.deb

```

than open with prefered package manager

or paste into terminal what you have been suggested above but replace gimp_2.2.4-2_i386.deb with gimpshop-2.2.11.deb

---

### Post by sparX CG on 2006-06-19
```
sparx@TBIRD1000:~$ sudo dpkg -i gimpshop-2.2.11.deb
(Reading database ... 74764 files and directories currently installed.)
Unpacking gimpshop (from gimpshop-2.2.11.deb) ...
dpkg: error processing gimpshop-2.2.11.deb (--install):
 trying to overwrite `/etc/gimp/2.0/gimprc', which is also in package gimp-data
Errors were encountered while processing:
 gimpshop-2.2.11.deb
```
Any help?  I'd like to get it working too...

---

### Post by zodwallop on 2006-06-22
```
dan@Dan-ubuntu:~$ sudo dpkg -i gimpshop-2.2.11.deb
Selecting previously deselected package gimpshop.
(Reading database ... 129216 files and directories currently installed.)
Unpacking gimpshop (from gimpshop-2.2.11.deb) ...
dpkg: dependency problems prevent configuration of gimpshop:
 gimpshop depends on libgimpprint1 (>= 4.2.7); however:
  Package libgimpprint1 is not installed.
dpkg: error processing gimpshop (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gimpshop

```

I'm running into errors as well.  Any new light one this issue would be awesome!

---

### Post by stangbang on 2006-06-22
you can get the package from here [http://packages.ubuntu.com/hoary/libs/libgimpprint1](http://packages.ubuntu.com/hoary/libs/libgimpprint1)

The deb package for gimpshop at [http://web.njit.edu/~st7/mirror/GIMPShop/gimpshop-2.2.11.deb](http://web.njit.edu/~st7/mirror/GIMPShop/gimpshop-2.2.11.deb) is also a little messed up. The package installs fine, but when you run gimp it starts looking for files in /home/suramya/Temp/GimpShop/gimpshop//share/gimp/2.0 I would suggest finding a different way to install this package. such as from source.

---

