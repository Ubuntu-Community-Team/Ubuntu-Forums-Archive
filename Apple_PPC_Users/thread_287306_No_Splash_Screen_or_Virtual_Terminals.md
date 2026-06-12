---
title: "No Splash Screen or Virtual Terminals"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by szim90 on 2006-10-28
Hello.

I just upgraded to Edgy, and I noticed that I can no longer can access virtual terminals (control + alt + F Key) - instead, a black and white distorted version of my previous screen appears. 

I also noticed that neither the startup nor the shutdown splash screens are working correctly. On startup, after the yaboot prompt, the screen goes completely white. Eventually the screen goes away and the login screen appears. On shutdown, the screen becomes a gray color.

The two problems started after I upgraded to Dapper from Breezy (in breezy, the usplash colors were distorted, but it did go show the splash and the startup information). 

I am using the nv video driver with a GeForce2 MX on a Quicksilver G4. I have upgraded usplash to the most recent version. 

Here is my yaboot.conf:
```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

```

Thank you for any help.

---

### Post by nikosp on 2006-11-17
I've just switched to linux (ubuntu edgy) and i have the same problem.. (ATI mobility radeon X700, but working with the vesa driver right now)

Removing the usplash from /boot/grub/menu.lst  solves the problem (Virtual terminals are OK) but then I have no boot splash  ;)

Any sugestions  ?  :confused:

---

### Post by jasont.t on 2006-11-20
I get the same problem when booting and shutdown (no splash screen).

My install of Edgy was a brand new install (no upgrade), and occurred from the word go; the only thing I kept was my home drive and all it's data.

Has anyone else had this issue and resolved it?

Thanks

---

### Post by davidshere on 2006-11-20
I also have no splash screen at startup or shutdown... not causing me any grief, but it does take away from the satisfaction of upgrading.

I'm not using yaboot. :-k

---

### Post by seatea on 2006-11-21
Look at this link.
[http://www.ubuntuforums.org/showthread.php?t=290998](http://www.ubuntuforums.org/showthread.php?t=290998)

---

