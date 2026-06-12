---
title: "tons of problems!?!"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Pap3rbag on 2008-01-19
well ever since i started running ubuntu  ive been having problems

- i dont have any widescreen resolutions at all

- i get input not supported whenver i boot it up 

- and now i cant even boot it i get this message

"anac (h)roristic cron anacrom

deferred execution scheduler

perodic command scheduler

checking battery 

running local boot scripts (ect/rc.local)" 

please somone help im pulling my freaking hair out :confused::confused:

---

### Post by mike23 on 2008-01-19
have u got the correct driver for ur video card ??

---

### Post by Pap3rbag on 2008-01-19
yes

---

### Post by xyz on 2008-01-20
[Someone solved it here...so hopefully....]("http://ubuntuforums.org/showthread.php?t=637261")

---

### Post by philinux on 2008-01-20
Boot the pc. when you see grub loading press esc.

Choose the recovery mode. When you get a command line enter this.

sudo dpkg-reconfigure -phigh xserver-xorg

This will reconfigure xorg for you.

then

sudo start x


Hope it gets fixed

---

