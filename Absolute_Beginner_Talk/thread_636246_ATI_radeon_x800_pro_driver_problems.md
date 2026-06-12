---
title: "ATI radeon x800 pro driver problems"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by james1030 on 2007-12-09
im fairly new to linux so please respond nOOb style. 
I have a dual monitor system and just loaded up ubuntu 7.10 and am having some trouble with the driver. i know there are a few threads already out there but my comp is just not cooperating. 
my goal here is to get 3d graphics online. ive tried enabling the accelerated graphics driver in the restricted drivers manager, i've also tried just about every other thread suggestion i can find. the problem is not that i cant get the ATI driver to activate, its that once i do, and restart the system, the first thing that pops up is and error saying "ubuntu is running in low graphics mode". its like 600x800, and my vid card (x800pro) goes way higher. if i try to configure the graphics and screens, when i restart it just says the same thing again "low graphics mode". 
i also have dual monitors(both 1440x900 lcd) which i would like to get "big desktop" working on, but the 3d is more important right now.
please help me i feel like i have tried everything.
thanks so much.

---

### Post by Majorix on 2007-12-09
I have a single-monitor system with the same video card and am running the open source radeon drivers without any problems.

---

### Post by james1030 on 2007-12-09
wish i could say the same. how dod you ghet your drivers to work, did you just use the preinstalled linux driver for ATI cards? does your 3D work?

---

### Post by Majorix on 2007-12-09
Yes, I used the pre-installed drivers. I haven't edited/added anything extra and yes 3D works.

Tough luck in your case :(

---

### Post by sloggerkhan on 2007-12-09
my guess is  that the initial xorg.conf for the fglrx driver is probably not correct. Manually configuring it is your best bet.

I trust you have done a dpkg-reconfigure xserver-xorg after installing the new driver?

the ATI (open source drivers) work okay for x700 and x800, but aren't quite up to snuff for games.

---

### Post by james1030 on 2007-12-09
"dpkg-reconfigure xserver-xorg"

no i havent done one, can you explain how to do it?
do i just enter that into the terminal?

thanks for your help i appreciate it.

---

### Post by sloggerkhan on 2007-12-09
enter it into a terminal like this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by james1030 on 2007-12-10
then what. it just runs me through a series, with no options or preferences. what was the purpose of it?

---

