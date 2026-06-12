---
title: "having trouble installing alsa-oss"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by mokmoki on 2006-09-11
i'm having trouble installing alsa-oss...

when i try the apt-get method, it says this:
......~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree... Done
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate

and i have no idea what the console is saying. it says the same thing everytime i use apt-get...

thanks for the help...

---

### Post by Hanj on 2006-09-11
Seems like something is wrong with your apt database. You might be able to solve this by running 'sudo apt-get -f install'.

---

### Post by mokmoki on 2006-09-11
i tried what you said, and this is what popped up...

...........:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then i tried "sudo apt-get install alsa-oss", and the same thing still happens...

off-t: i'm really a newb in linux but i'm very willing to learn... i want something new, i'm tired of windows...

---

### Post by mokmoki on 2006-09-11
never mind, i figured out the problem... 

sorry for the inconvenience for such a stupid problem ^_^

just forgot to enable universe, multiverse and backports....

---

