---
title: "[SOLVED] A clean install of Arch, what to do now...."
date: 2008-12-12
forum: Arch and derivatives
---

### Post by gjoellee on 2008-12-12
I have installed Arch Linux successfuly and set up a user, it is time to install the desktop I want (xfce), but i somehow can't. I am at the command line adding the following command:
```
pacman -S xfce4
```
 and I get this output:
> error: 'xfce4' : not found in sync db

what can I do? (I still only have the command line)

---

### Post by Majorix on 2008-12-12
Make sure you are connected to the net and run
```
sudo pacman -Syy
sudo pacman -Su
```
and then you can use pacman to install/uninstall software.

---

### Post by gjoellee on 2008-12-12
> **Majorix said:**
> Make sure you are connected to the net and run
```
sudo pacman -Syy
sudo pacman -Su
```and then you can use pacman to install/uninstall software.

this is what happens:
```
error: failed retreiving file "core.db.tar.gz" from ftp.archlinux.org : transmission resolver failure
```

I should be connected, I have plugged in a cable and rebooted

---

### Post by albinootje on 2008-12-12
Can you succesfully ping this one : ping.xs4all.nl ?
And you should check the pacman config, because ftp.archlinux.org is throttled by default, it's better to use a mirror.

Read also this : [http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)

---

### Post by gjoellee on 2008-12-12
got it working now

---

