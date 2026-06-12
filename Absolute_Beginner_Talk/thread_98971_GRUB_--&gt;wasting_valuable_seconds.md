---
title: "GRUB --&gt;wasting valuable seconds"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by ashrack on 2005-12-04
I really have no idea why it takes 5seconds for the GRUB to load to the OS selection screen?
Is there any fix for it?

---

### Post by grimmson on 2005-12-04
I think thats just part of boot-up. You may try optimizing you bios (boot order, etc...)

---

### Post by d1337 on 2005-12-04
edit this part of /boot/grub/menu.lst
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10
```

change the timeout to your liking.

d1337

oops...obviously didn't read into your post all the way.  Sorry, but I do think that editing your boot order in bios is your only way to shorten it...and it likely won't be immediate

---

### Post by az on 2005-12-04
[QUOTE=ashrack]I really have no idea why it takes 5seconds for the GRUB to load to the OS selection screen?
Is there any fix for it?[/QUOTE]

Comment out the hiddenmenu so that it automatically goes to the menu.  Then set your timout to one second.


## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

---

### Post by Chickenmonger on 2005-12-04
Although it is tempting, don't put the timeout on the boot selection screen to zero for a non-dual-booting system. A kernel upgrade might bork your system, and you will want the ability to boot a past kernel.

---

### Post by ashrack on 2005-12-05
[QUOTE=grimmson]I think thats just part of boot-up. You may try optimizing you bios (boot order, etc...)[/QUOTE]
BIOS is optimized and set do boot from HDD firtst. And also w/ Win2k boot loader I got to the OS selector screen in a second

---

### Post by ashrack on 2005-12-05
[QUOTE=azz]Comment out the hiddenmenu so that it automatically goes to the menu.  Then set your timout to one second.


## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu[/QUOTE]

It already was commented.
Here's the file:
[http://www2.arnes.si/~aurank1/menu.lst](http://www2.arnes.si/~aurank1/menu.lst)

---

