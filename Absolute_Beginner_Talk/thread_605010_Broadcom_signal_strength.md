---
title: "Broadcom signal strength?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Avinash4 on 2007-11-06
i'm currently dual booting windows xp and ubuntu, but sometimes i cannot connect to my school network using ubuntu, but if i boot windows, i can connect fine. i have a broadcom wireless card, and i installed the non-standard drivers when i was prompted by ubuntu 7,10. occasionally i can connect, but the browsing is very lagged (like right now).

---

### Post by rudeboyskunk on 2007-11-06
Broadcom does not release their hardware information, so no open source drivers can be written for their stuff.  This means that half the time their hardware either will not work under Linux, or will work less than awesome.

Did you use ndiswrapper to install the drivers?

---

### Post by garethpaul on 2007-11-06
I'm getting the exact opposite. I have a network that I am borderline on the range of - Windows Vista can see it but will only connect to it with limited connectivity - basically useless. However, a reboot into Ubuntu and it connects at about 48-50% strength with good transfer speeds.

---

### Post by rudeboyskunk on 2007-11-06
> **garethpaul said:**
> I'm getting the exact opposite. I have a network that I am borderline on the range of - Windows Vista can see it but will only connect to it with limited connectivity - basically useless. However, a reboot into Ubuntu and it connects at about 48-50% strength with good transfer speeds.

Add it to the list of stuff Vista sucks at.

---

### Post by Avinash4 on 2007-11-06
> **rudeboyskunk said:**
> Broadcom does not release their hardware information, so no open source drivers can be written for their stuff.  This means that half the time their hardware either will not work under Linux, or will work less than awesome.

Did you use ndiswrapper to install the drivers?

i'm a linux noob, so i have no clue what ndiswrapper is. all i know is a window came up when i first installed ubuntu called: restricted drivers manager. it basically said, due to licensing reasons lots of drivers are not included with ubuntu, would you like to upgrade to the restricted drivers, and there was by broadcom card in the list, and i put a checkmark beside it, and it auto-installed.

---

### Post by Llewellyn01 on 2007-11-06
> **Avinash4 said:**
> i'm a linux noob, so i have no clue what ndiswrapper is. all i know is a window came up when i first installed ubuntu called: restricted drivers manager. it basically said, due to licensing reasons lots of drivers are not included with ubuntu, would you like to upgrade to the restricted drivers, and there was by broadcom card in the list, and i put a checkmark beside it, and it auto-installed.

To quote an old engineer I once worked with, if it ain't broke don't try and fix it.

Windows deals with its TCP/IP stack badly. If its laggy, it might be the wireless protocol and nothing really to do with the wireless card itself or just network traffic. I know Linux can be a little funny with WPA and WPA2 (but to be fair its not given me much grief). 

Best thing might just be to disconnect and reconnect something I do alot with our new Vista boxes.

Cheers

Rich

P.S. I am a linux newbie I work with windows but growing to love Linux :-)

---

### Post by Papa-san on 2007-11-06
I use a program called 'Wicd'
Here's the link:
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)
It works well once the Bcom drivers are working.

Ndiswrapper is prolly the only decent way to get the drivers working.

---

