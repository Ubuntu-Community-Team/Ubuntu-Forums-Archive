---
title: "bus error core dumped"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-12-19
when i open up Synaptic Package Manager, it opens and then closes
when i open add/remove it opens and then closes
apt-get upgrade gives me:

billybag@billybag-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Bus error (core dumped)e... 0%



 whats up?

---

### Post by billybag on 2006-12-19
nedvermind. dpkg --configure -a fixed it

---

