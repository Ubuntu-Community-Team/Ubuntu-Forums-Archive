---
title: "Can't open cli in Xubuntu"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by tava0002 on 2008-01-31
I just installed Xubuntu 7.10 on an older Optiplex GX150. When I try to open the cli from "Apps - Accessories - Terminal", it brings up another login screen for xfce.

I've never had this problem, granted, I usually install Ubuntu desktop.

Also, when I try to download something(Terminal) from "Add/Remove apps" I get 

"Terminal cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."



I'm starting to think Xubuntu wasn't the right choice for this machine.

---

### Post by tava0002 on 2008-02-01
Fixed.

---

### Post by mali2297 on 2008-02-01
> **tava0002 said:**
> Fixed.

:-s How? (It might be of help to others.)

---

### Post by Cochise on 2008-02-01
yes how? please when i open the terminal in xbuntu on my older machine it restarts X

---

### Post by mali2297 on 2008-02-01
> **Cochise said:**
> yes how? please when i open the terminal in xbuntu on my older machine it restarts X

I can answer this. :-)

It is a known bug, see
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)
[http://ubuntuforums.org/showthread.php?t=605869?post=#8](http://ubuntuforums.org/showthread.php?t=605869?post=#8)

---

### Post by tava0002 on 2008-02-01
Yes, a friend informed me that it is a known issue, I have not had the time to try it.  He suggested ctrl+alt+f2 to get to the cli and do an apt-get of Konsole, orr edit the xorg.conf file and change the default depth from 24 to 16.

---

