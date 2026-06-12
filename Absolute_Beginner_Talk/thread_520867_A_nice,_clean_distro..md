---
title: "A nice, clean distro."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-08-08
I am looking for a nice, clean distro. I want it to have a desktop enviornment, synaptic, and very little basic software. I want to add the software myself. No media players or anything like that. Are there any distros like this?

//izizzle

---

### Post by amazingtaters on 2007-08-08
You could always install *buntu and then remove what you don't need.t

---

### Post by Majorix on 2007-08-08
I believe there was a way to install Ubuntu from "bone". That way you will have very few software, and most likely a faster system. The only problem is that I don't have the link to that site anymore :( But I am sure someone around does.

---

### Post by bodhi.zazen on 2007-08-08
Something like this : [http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

You can do a minimal install then add X + Fluxbox/Openbox + anything else you need.

You might also like [Arch Linux](http://www.archlinux.org/)

---

### Post by izizzle on 2007-08-08
I want to boot up to a graphical enviornment with very liitle software....like synaptic.

---

### Post by ron999 on 2007-08-08
...............

---

### Post by bodhi.zazen on 2007-08-08
It is not hard ...

You need to be comfortable with the command line is all.

It is far easier to do a minimal install and add then a full install and remove.

See here for some advice :

[http://ubuntuforums.org/showthread.php?t=517641](http://ubuntuforums.org/showthread.php?t=517641)

Then, for example, 

Server install: aptitude install x-window-system-core gdm eterm (WM here)<fluxbox, icewm, wmaker, openbox... are good light weight WM's.

	Dapper :

		Fluxbox: aptitude install x-window-system-core gdm eterm fluxbox fluxconf

	Edgy ++
		
		Fluxbox : aptitude install xorg wdm eterm fluxbox fluxconf


Feisty :
		[http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)


See that last link :twisted:

---

### Post by RedSquirrel on 2007-08-08
More links:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by izizzle on 2007-08-08
I've found the one! E17(elive). Good looking, basic software, lightweight, fast, and debian based! WOOT!

Thanks for the help though, guys.

---

### Post by asmoore82 on 2007-08-08
go for archlinux !!!
I used to be able to install it fairly quickly but I installed it for my g/f for the first time in like a
year and a half and it never quite acts right ... it won't detect my usbdrive or her mp3 player cell phone
she is getting a fresh Ubuntu format as we speak.

archlinux is superb if you can take the time to learn it.

---

### Post by kellemes on 2007-08-10
> **asmoore82 said:**
> go for archlinux !!!
I used to be able to install it fairly quickly but I installed it for my g/f for the first time in like a
year and a half and it never quite acts right ... it won't detect my usbdrive or her mp3 player cell phone
she is getting a fresh Ubuntu format as we speak.

archlinux is superb if you can take the time to learn it.

Agree.. Arch is not too hard and much fun to setup, even for starters. As long as you take your time..

But since he wants synaptic.. I would go for Debian for sure, it's the mother of *buntu, somewhat more reliable and predictable and certainly much cleaner then *buntu.. out of the box that is..

---

