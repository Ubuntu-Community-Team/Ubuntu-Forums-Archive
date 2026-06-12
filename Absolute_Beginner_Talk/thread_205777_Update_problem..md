---
title: "Update problem."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-29
In my ubuntu task bar there was a notification that **new updates available**.
So i clicked and checked the updates that i wanted and then when i clicked on install. I got this error.

> 
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)



---

### Post by amohanty on 2006-06-29
In a terminal APplications->Accessories->Terminal, type the following:
> sudo apt-get update

provide your password and and wait for it to finish. Try the update double click thingy again.

HTH
AM

---

### Post by hardfire_avk on 2006-06-29
[QUOTE=amohanty]In a terminal APplications->Accessories->Terminal, type the following:


provide your password and and wait for it to finish. Try the update double click thingy again.

HTH
AM[/QUOTE]

Done dut didn't help!!

---

### Post by amohanty on 2006-06-30
Can you hit this url from the problem machine:
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/)

AM

---

