---
title: "Dual Booting"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Scubastev013 on 2007-05-08
I have a Dell Inspiron E1505 with Windows Home Premium Preinstalled.  I would like to install 7.04 and dual boot the machine.  The only thing is, I would like to use the windows bootloader.  I'm more comforatable with the windows loader, and if the computer ever needs servicing, it will be easier on them.  The goal is to have vista boot automatically, unless i catch it with F12 or whatever it is.  I installed 7.04 on my XP machine, but was not sucessful in getting xp to boot first without me having to catch it.  I would the exact code for what I need to change or whatever.


Thanks,

Scuba

---

### Post by Cypher on 2007-05-08
If you search Google for this, you'll find countless sites that will provide you the step-by-step instructions, but take it from any of us who's done it both ways that installing GRUB is so much easier than making the Windows bootloader care about anything but itself.

Additionally, you could install GRUB and have it default to load Windows all the time, the bootloader is such a small piece of code that it, in no way, will interfere with the Windows operation or bootup.

---

### Post by eltorodeoro on 2007-05-08
I concur with Cypher.  GRUB is a fantastic utility.  NTLDR on the other hand, not so much.

---

### Post by confused57 on 2007-05-08
Grub is a great bootloader and easier to configure...thought I'd reply here since you weren't getting any replies in your other thread:
[http://ubuntuforums.org/showthread.php?t=436931](http://ubuntuforums.org/showthread.php?t=436931)

Maybe this is what you're looking for:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

See the section about default OS at boot in grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

