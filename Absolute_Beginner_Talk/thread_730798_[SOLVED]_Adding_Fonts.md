---
title: "[SOLVED] Adding Fonts"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by rcdeacon on 2008-03-21
I have just installed Hardy on my laptop. I am trying to install some additional fonts to my system but I have a permissions problem. The additional fonts are in my home folder but I cannot copy them to /usr/share/fonts/truetype. I may need to be root but I do not know how to enable the root account.

---

### Post by keratos on 2008-03-21
> **rcdeacon said:**
> I have just installed Hardy on my laptop. I am trying to install some additional fonts to my system but I have a permissions problem. The additional fonts are in my home folder but I cannot copy them to /usr/share/fonts/truetype. I may need to be root but I do not know how to enable the root account.

If you are using the account login name supplied at install then enter:
```

sudo <command>

```
e.g.
```

sudo cp myfonts/* /usr/share/fonts/truetype
sudo dpkg-reconfigure fontconfig

```

sudo is a way to temporarily gain root privilages. You will be asked to enter your password which is saved after the first time in any given X session.

the dpkg-reconfigure is a debian package (dpkg) reconfiguration of the fontconfig package. Part of he reconfiguration process for this package is to trigger the font server to reload your fonts from the font dirs specified in /etc/X11/xorg.conf. So make sure your fontpath, in your case /usr/share/fonts/truetype is in the xorg.conf file.

p.s. Hardy is experimental/unstable. If you dont know how to do the above then I would question with respect, why you installed an unstable linux distro. If you want to learn about linux then you have selected an appropriate path !!!

---

### Post by kostkon on 2008-03-21
> **rcdeacon said:**
> I have just installed Hardy on my laptop. I am trying to install some additional fonts to my system but I have a permissions problem. The additional fonts are in my home folder but I cannot copy them to /usr/share/fonts/truetype. I may need to be root but I do not know how to enable the root account.

You can just copy them to your *.fonts* folder.

---

### Post by keratos on 2008-03-21
> **kostkon said:**
> You can just copy them to your *.fonts* folder.

Correct.

Dang, I always go for the difficult option !!

:lolflag:

---

### Post by rcdeacon on 2008-03-21
Kostkon,
Thanks, that fixed the problem.

---

