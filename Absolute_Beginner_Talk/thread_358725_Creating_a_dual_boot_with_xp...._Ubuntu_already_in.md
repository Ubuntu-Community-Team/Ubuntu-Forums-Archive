---
title: "Creating a dual boot with xp.... Ubuntu already installed though"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Xantra on 2007-02-11
Hi,

As the title suggests, i already have Ubuntu version 6.06 installed on my machine. Im currently running a windows xp VM using VMware but im running into some performance issues when i use programs which require more resources which is a bit annoying. 

Im aware that the easiest way to create a dual boot of xp and windows is to have windows installed first? I could be wrong though? Im wondering if theres any guides out there or tips on how best to do it with ubuntu already in place. I dont really want to wipe what I have at all so starting from scratch isnt something I would consider.

Any ideas?

Cheers.

---

### Post by meng on 2007-02-11
If you install Windows second, it will overwrite the master boot record and you won't be able to boot Ubuntu. However, this is easily fixed!
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Xantra on 2007-02-11
OK from a quick read of that I'm taking it that I need to first install XP, and then run the ubuntu live cd and fire off a few commands through the terminal?

---

### Post by meng on 2007-02-11
Yep, it should be that easy.

---

### Post by Xantra on 2007-02-12
that worked great, thanks :)

---

### Post by nickburns on 2007-02-12
Just a thought, you may want to go the VMware route.  They there is no more rebooting required to get from one OS to another.

---

### Post by Xantra on 2007-02-15
As I said I had performace issues. I'll retain my VM though.


Heres a writeup of what I went through to do this. 

[http://chris-gallagher.com/2007/02/12/creating-a-windows-xp-ubuntu-dual-boot-system-with-ubuntu-already-installed/](http://chris-gallagher.com/2007/02/12/creating-a-windows-xp-ubuntu-dual-boot-system-with-ubuntu-already-installed/)

If anyone has any corrections please point them out :)

---

