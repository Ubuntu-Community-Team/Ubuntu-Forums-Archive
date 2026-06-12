---
title: "Dapper Beta 2:  desktop icons"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by n3tfury on 2006-05-08
I just installed my first custom icon set and would like to enable desktop icons (drives, etc), but do not see how to do this.  Breezy's instructions do not apply here.

---

### Post by ComplexNumber on 2006-05-08
[quote=n3tfury]I just installed my first custom icon set and would like to enable desktop icons (drives, etc), but do not see how to do this.  Breezy's instructions do not apply here.[/quote] they appear automatically when the device(cd, dvd, usb, floppy, etc) has been inserted into the drive and mounted. thats how it is on gnome.

---

### Post by n3tfury on 2006-05-08
that makes sense, but what about the Computer, Home, and Trash icons?

---

### Post by ComplexNumber on 2006-05-08
[quote=n3tfury]that makes sense, but what about the Computer, Home, and Trash icons?[/quote] don't they appear? if not, do this:
-go to gconf editor (or type in 'gconf-editor' on the command line)
-go to the main menu and select the 2nd menu
-select 'Find'
-you will see 2 tick boxes. leave them unticked. type in 'nautilus' and press RETURN key.
-the 2nd one down shoud be '/apps/nautilus/desktop'
-tick the icons that you want to appear on your desktop.

---

### Post by n3tfury on 2006-05-08
you, my friend, just put a smile on my face.  thanks alot for your help.  seems a bit more work compared to breezy.  

you questioned whether they appeared or not by default?  is that how it's supposed to be in Dapper?  this is a 2 day old install, so i'm sure i didn't inadvertantly remove them.

thanks again, bro.

aloha

---

### Post by ComplexNumber on 2006-05-08
> s that how it's supposed to be in Dapper? i don't know about dapper because i haven't tried it. but i currently use fedora core 5 and they appear by default in that. both use gnome 2.14.

glad to help :)

---

