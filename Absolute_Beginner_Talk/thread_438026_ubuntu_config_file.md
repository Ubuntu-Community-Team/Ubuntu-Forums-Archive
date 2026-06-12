---
title: "ubuntu config file"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by moon_dog on 2007-05-09
this is kind of a newb question... but where is ubuntu's main config file?  in arch linux it's rc.conf, which is stored in /etc/.  can't find it on ubuntu

---

### Post by mejy on 2007-05-09
Ubuntu uses a more modular system, and I can't think of any file that replaces RC.  Rather, it's spread over multiple files.  If there's anything in particular you want to configure, either post back or google it and you should be able to figure out the necessary config files.  The general trend seems to be moving from ubiquitous config files to a more structured system (I know that Gentoo has implemented a similar change, for example).

---

### Post by moon_dog on 2007-05-09
ok, so what file controls which daemons and services start in the beginning?  say i would like to include a script to the startup process.

---

### Post by ikonia on 2007-05-09
if your using arch linux you should be aware of system V init.

ubuntu uses either system V init (ubuntu 6.06) or "upstart" (6.10 or greater)

these scripts are in /etc/init.d and has the same run level technique as arch linux, so I'm not sure why your confused. If your using 6.10 or greater I'd suggest you view the docs on upstart before meddling.

---

### Post by girishv on 2007-05-09
you can actually create a file by name rc.local in /etc and it will be read everytime ubuntu boots. If you want to
add it into a particular level, just check out the directories /etc/rc?.d where ? is from 0 to 6 and S. If I remember correctly, ubuntu uses rc2.d for login into X-windows

Girish

---

