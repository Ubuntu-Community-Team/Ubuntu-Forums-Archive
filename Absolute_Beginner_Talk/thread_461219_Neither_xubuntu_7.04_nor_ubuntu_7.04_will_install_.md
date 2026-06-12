---
title: "Neither xubuntu 7.04 nor ubuntu 7.04 will install on my old laptop"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-06-01
Hi
Situation: 
I'm trying to install xubuntu 7.04 on an older laptop (asus M2000), have ubuntu 6.10 installed at the moment but want to try out xubuntu.
I have tried: 
- xubuntu 7.04 desktop, 
- xubuntu 7.04 alternate, 
- ubnutu 7.04 desktop, 
- ubuntu 7.04 alternate (I've used this cd for the installation on the machine I'm sitting at right now)

xubuntu 7.04 desktop, xubuntu 7.04 alternate:
The boot screen shows as expected. After starting the install (both standard install and safe graphics mode) it appears to initiate the install process (some green text and some dots at top edge of the screen) then screens turns black with a blinking dash in top left corner and nothing happens.

ubnutu 7.04 desktop:
The boot screen shows as expected.  After starting the install (both standard install and safe graphics mode) it appears to initiate the install process (as above) then (with the menu still visible) it stops reporting in green text at top of screen "invalid or corrupt kernel image". When selecting one of the menus it reports "Could not find kernel image".

ubuntu 7.04 alternate
The boot screen shows as expected. After starting the installation the screen blinks a few times and it reboots (returning to the boot screen).

I suspect some kind of incompatibility between my old asus m2000 and feisty?

Any suggestions what I can do to try out xubuntu?

---

### Post by dpzektor on 2007-06-01
I could be wrong, but it sounds like bad memory to me. Do you have another memory module at your disposal?

---

### Post by kernel tom on 2007-06-01
what are the specs on ur system? even tho xubuntu is light it still has requirements

---

### Post by fsando on 2007-06-01
That was fast! :)
It's running ubuntu 6.10 with no hickups
It's a centrino 'core one' 1.3 ghz 500mb ram 40 gb hd. So it's not a specs problem as such.

I found others having similar problems here:
[http://ubuntuforums.org/showthread.php?p=2762390#post2762390](http://ubuntuforums.org/showthread.php?p=2762390#post2762390)
They advice to 'F6' and add ACPI=OFF. I tried it with the same result.

A bit more informations though: if I delete 'quiet' from the parameter line it stops right after
```
[   48.900641] PCI: Using configuration type 1
[   48.900694] Setting up standard PCI resources
```

Oh btw I did an extensive memory test because I too thought it could be a memory problem.

---

### Post by fsando on 2007-06-01
Latest update:
I'm now posting from the 'problem machine'.
I'm installing xubuntu 6.10 right now, so I guess it's a feisty problem - which I suspected all along - of all those kernel issues.
I'll try to update from 6.10 to 7.04 later

UPDATE:
Xubuntu 6.10 installed without a hitch
I then upgraded to xubuntu 7.04 with kernel 2.6.20-16, which resulted in the laptop constantly rebooting (without any user interaction). 

So the obvious conclusion is that  my laptop does not work with feisty!

---

### Post by fisheryu on 2007-12-24
> **fsando said:**
> That was fast! :)
It's running ubuntu 6.10 with no hickups
It's a centrino 'core one' 1.3 ghz 500mb ram 40 gb hd. So it's not a specs problem as such.

I found others having similar problems here:
[http://ubuntuforums.org/showthread.php?p=2762390#post2762390](http://ubuntuforums.org/showthread.php?p=2762390#post2762390)
They advice to 'F6' and add ACPI=OFF. I tried it with the same result.

A bit more informations though: if I delete 'quiet' from the parameter line it stops right after
```
[   48.900641] PCI: Using configuration type 1
[   48.900694] Setting up standard PCI resources
```

Oh btw I did an extensive memory test because I too thought it could be a memory problem.

I had the same problem with an asus m2000 laptop. I've check the referred thread, the last post indicated adding a "nolapic" option and it works. :lolflag:

---

