---
title: "What version of U. am i running?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by darenw on 2006-07-02
Though i'm not a total beginner with Ubuntu, and many years with Linux in general, this is definitley a newbie-esque question:  what is the proper official way to tell what version of Ubuntu i'm running?    Izit Breezy/Hoary/...?   and who makes up these names, anyway?   :?

---

### Post by bikeboy on 2006-07-02
"cat /etc/issue" or issue.net

---

### Post by manicka on 2006-07-02
System-->About Ubuntu

---

### Post by Jucato on 2006-07-02
The "names" Warty Warthog, Hoary Hedgehog, Breezy Badger, and Dapper Drake are sort of "development" codenames, just like Longhorn is the codename of MS Windows Vista. 

The official "names" really are Ubuntu 5.10, Ubuntu 6.06 LTS,  etc.

Btw. the next version, Ubuntu 6.10, is codenamed Edgy Eft. :D

---

### Post by darenw on 2006-07-02
i tried System->About Ubuntu, but it brought up what looked like only generic Ubuntu information.

cat /etc/issues works fine - but there's no easily discoverable GUI way that would be obvious to rank beginners?   maybe an applet in the toolbar (or whatever the gnome people call it) next to the date/time/whatever.   

anyway, i'm happy with the answer to this.   Ubuntu forums are the fastest i've seen anywere!

---

### Post by Jucato on 2006-07-02
[QUOTE=darenw]i tried System->About Ubuntu, but it brought up what looked like only generic Ubuntu information.[/QUOTE]

The first line of the Help window that opens says:
> Thank you for your interest in Ubuntu 6.06 LTS - the *Dapper Drake* - released in June 2006.

---

### Post by uzi09 on 2006-07-03
or in console/terminal:

```
lsb_release -a
```

---

### Post by FredB on 2006-07-03
For a Dapper (I can't use 6.06 LTS name !) you got :

```

fred@fredo:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper

```

---

