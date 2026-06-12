---
title: "Difference between PC-BSD and FreeBSD"
date: 2008-07-10
forum: BSD
---

### Post by kk0sse54 on 2008-07-10
I've used both and I am aware that PC-BSD is based off FreeBSD but what are the major differences between the two other than of course PC-BSD seems to be a lot more user friendly oriented more for BSD beginners.

---

### Post by cardinals_fan on 2008-07-10
_PC-BSD_
* Based off FreeBSD
* GUI (KDE) and graphical config tools by default
* PBI package management.  It should be possible to install FreeBSD ports on PC-BSD, but they prefer that you use the PBIs.

_FreeBSD_
* Command-line install, add your own GUI
* No graphical tools, if you install a DE it will include its own
* Uses ports to install software.  Enormous selection of ports available.

_DesktopBSD_
* Essentially vanilla FreeBSD with KDE by default and some graphical config tools
* Uses FreeBSD ports for software installation.  Same vast selection.
* Stays very true to FreeBSD.

---

### Post by kk0sse54 on 2008-07-10
So pretty much from what I am gathering from everything that I have read PC-BSD is still FreeBSD under the hood. I really liked the idea of PBIs except I was expecting to find a lot more software selection which basically means that I have to use ports to get the software I want. It makes more sense then to just run FreeBSD because I really don't like KDE because I find it way too bloated, confusing, etc etc and other desktop environments for the most part don't seem to run too well. The only other thing that Pc-BSD has over FreeBSD is its simplicity but I don't mind getting my hands dirty since I've already done it once. Thanks mate :)

---

### Post by cardinals_fan on 2008-07-10
> **C!oud said:**
> So pretty much from what I am gathering from everything that I have read PC-BSD is still FreeBSD under the hood. I really liked the idea of PBIs except I was expecting to find a lot more software selection which basically means that I have to use ports to get the software I want. It makes more sense then to just run FreeBSD because I really don't like KDE because I find it way too bloated, confusing, etc etc and other desktop environments for the most part don't seem to run too well. The only other thing that Pc-BSD has over FreeBSD is its simplicity but I don't mind getting my hands dirty since I've already done it once. Thanks mate :)
IMHO, DesktopBSD > PC-BSD.  It's a much purer FreeBSD under the hood.

---

### Post by Sorivenul on 2008-07-15
> **cardinals_fan said:**
> imho, Desktopbsd > Pc-bsd.  It's A Much Purer Freebsd Under The Hood.

+1

---

### Post by angryfirelord on 2008-07-28
Unfortunately, there hasn't been much movement in the DesktopBSD project lately and development tends to move very slowly. However, if you do want to install straight FreeBSD, you can always install DesktopBSD's tools in /usr/ports/sysutils/desktopbsd-tools/.

---

### Post by cardinals_fan on 2008-07-29
> **angryfirelord said:**
> Unfortunately, there hasn't been much movement in the DesktopBSD project lately and development tends to move very slowly. However, if you do want to install straight FreeBSD, you can always install DesktopBSD's tools in /usr/ports/sysutils/desktopbsd-tools/.
They're slow, but definitely not dead.

---

