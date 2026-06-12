---
title: "[Mint 10] The system freezes after the touchpad is turned off"
date: 2010-12-20
forum: Any Other OS
---

### Post by dumitru on 2010-12-20
I'm working in Linux Mint 10. Every time I turn off the laptop's touchpad the system acts weird. Windows freeze, I cannot move them, they are stuck. The right click doesn't work. The left click sometimes selects the text etc. 

The problem disappears after I Logout or restart my laptop.

I think that the problem is with my drivers. In Windows I don't encounter problems (with the default Synaptics touchpad drivers).

------------------
Laptop HP Pavilion DV6646US • 1.9 GHz AMD Turion 64 X2 • 2048 MB DDR2 • NVIDIA GeForce Go 7150M up to 559MB • 160 GB (5400 RPM) (SATA) • LightScribe 8X DVD±R/RW • 15.4" WXGA (1280 x 800) • 10/100BASE-T Ethernet LAN • Wireless LAN 802.11a/b/g/n

---

### Post by Ziyan Junaideen on 2011-01-15
I have the same problem, Using Ubuntu 10.1 64bit.

When I turn off the touchpad, Widnows and Menues stop responding to clicks. Its posible to open up applications using the quick launch (ex: terminal) but can't do any thing with them.

I am on a DV6 1315TX laptop.

The problem with me is that, once I do reach such state, the laptop will not go pass the login screen, which I think is solvable via some Kernel Parameters. [http://ubuntuforums.org/showthread.php?p=10351435#post10351435](http://ubuntuforums.org/showthread.php?p=10351435#post10351435)

Some where I saw a post saying to remove some package that is to deal with laptop input devices and was regarding Ubuntu 10.1Beta I guess. But now I can't find that post.

---

### Post by jengelsm on 2011-02-12
I am having the same problem, on my DV9417ca, running Ubuntu 10.1 and it is particular to when I disable the touch pad in favour of my mouse, I can use the mouse mostly, I can open and close programs, however I can not access any menus, OS or the programs, and I can not type, and a forced reboot is necessary to get it back. if I start the computer with the touch pad off and just use the mouse, everything works fine

---

### Post by oktapod on 2011-03-29
Try this

Run:
gconf-editor

search for 'touchpad' by going on Edit -> Find-> then type touchpad

click on the first entry and click on the 'touchpad_enabled' checkbox twice.
set it on "true". If it is already set it to "false" then back to "true"

[http://ubuntuforums.org/archive/index.php/t-1470117.html](http://ubuntuforums.org/archive/index.php/t-1470117.html)

---

