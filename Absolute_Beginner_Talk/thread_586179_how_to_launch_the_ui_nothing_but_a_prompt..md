---
title: "how to launch the ui? nothing but a prompt."
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by denderaryuba on 2007-10-22
new linux/ubuntu user here.
i just installed kubuntu (7.04) on my dell 710m.
when i boot up, all i get is a command prompt. (and i only remember a few *nix commands from my college days)
how do i launch the desktop environment?
how do i make it launch automatically on boot?

(i actually have installed twice now, once with ubuntu-desktop and once with kubuntu. both have done the same thing)

thanks.:confused:

---

### Post by LanDan on 2007-10-22
you sure you installed the desktop version?

what happens if you type

startx

---

### Post by aysiu on 2007-10-22
This should help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by denderaryuba on 2007-10-22
tells me it doesn't exist, use apt-get to install it.
which i did.
now i get other errors when i 'startx'

etc/xll/x (no such file ...)

 i guess something went bad with my installation? sounds like things are missing.

[i'm trying aptitude install kubuntu-desktop now, thanks for helpful responses]

--david

---

### Post by LanDan on 2007-10-22
if it doesn't exist you can install it.
i just looked at the link from aysiu and it looks pretty good

just do 
sudo apt-get update
sudo apt-get install kubuntu-desktop

or

sudo apt-get install ubuntu-desktop

or 

sudo apt-get install xubuntu-desktop

---

### Post by Flying caveman on 2007-10-22
try 

> sudo dpkg-reconfigure xserver-xorg

enter your password and see what happens

---

