---
title: "where 2 dl libasound2&amp;libc6?"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by vvnoob on 2005-12-02
I have problems with installation java. System ask for libasound2 =>1.0.9 i have 1.0.8-1 and libc6=>2.3.4-1 i have 2.3.2ds-1-20 ubuntu

I prefer manuall dl becouse synaptic allways answer me that i have newest version and abort dl.

I dont need info about how to install java. I stuck only with this 2 packages.

TNX

---

### Post by frodon on 2005-12-02
libc6 is a really important package and a lot lot of your ubuntu packages are dependant of your current version of libc6, so changing the version of libc6 will break many packages.
That's one of the disadvantage of ubuntu, if you really want this release of java you could  post a request to the backport team.

---

### Post by vvnoob on 2005-12-02
I dled this 2 packages but during inatalacion i become this:

dpkg -i /home/charlie/Desktop/libasound2_1.0.10-1_i3 86.deb
dpkg: regarding .../libasound2_1.0.10-1_i386.deb containing libasound2:
 libasound2 conflicts with libasound2-plugins (<< 1.0.9)
  libasound2-plugins (version 1.0.8-1) is installed.
dpkg: error processing /home/charlie/Desktop/libasound2_1.0.10-1_i386.deb (--ins tall):
 conflicting packages - not installing libasound2
Errors were encountered while processing:

:confused:  what now?

---

### Post by frodon on 2005-12-02
That's what i meant when i said that you will get dependencies problems because of libc6.
The only thing you can do is to request your version of java to be backported, or test drapper drake which i think have the needed version of libc6 or ... switch to another distro like gentoo.

[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

---

