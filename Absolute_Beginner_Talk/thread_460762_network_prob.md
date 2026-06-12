---
title: "network prob"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by FKi on 2007-06-01
i need to connect to the internet.  Computer A has a wireless connection to my router, and is runnin windows xp. Computer B is running ubuntu, and connected to Computer A.   i cant seem to get it to work.. any suggestions?

---

### Post by khardbored on 2007-06-01
How is your ubby machine connecting to your XP machine? WIred/Wireless? Does the ubby machine have a wireless card? If so, just connect it wirelessly to the same router as A?

---

### Post by FKi on 2007-06-01
yeah the ubunt comps hard wired to the xp.

and the ubby comp has wireless, i just cant get it to work yet.

---

### Post by khardbored on 2007-06-01
Ok, so the ubby PC has wireless? Which wireless card are you using? If you don't know, try running "lspci" and searching for your card there. Also, when you say you cant get the wireless working on the ubby machine, why can't you? What have you tried, what errors, etc? Have you tried System/Administration/Network?

---

### Post by FKi on 2007-06-01
When i lspci it brings it up as "Atheros communications, inc.: unknown device 001c (rev 01)

as for what iv tried, really nothing because al li can find in the forums doesnt relate to my system, and in networking, it doesnt even show it up, so for right know im trying to go through the xp pc (plus i kinda wanted to learn how to do it this way)   

but yeah if i could fix the wireless as well as figure this mess out that would be fantastic

---

### Post by oreb on 2007-06-01
Can you ping your router?  Can you ping your xp machine?  Is internet connection sharing enabled on your xp machine?

---

### Post by FKi on 2007-06-01
i have it set up to the computer, it detects it but its "limeted or no connection"   and no i cant ping router or comp

intenet sharing is enabled

---

### Post by khardbored on 2007-06-01
From what I've read, it sounds like that chipset isn't supported...
::edit::
More reading, it may be supported via madwifi...hrm, not too sure. Might want to google this..

---

### Post by oreb on 2007-06-01
In terminal, run ifconfig and show me the results.

---

### Post by FKi on 2007-06-01
gotta remember ubuntus on another computer, but ill try my hardes to translate
eth             Link encap:Ethernet  HWaddr 00:13:a9:4e:f9:02
                  inet aaddr:192.168.1.105  Bcast:192.168.1.255 Mask: 255.255.255.0
                  inet6 addr: fe80::213:a9ff:fe4e:f902/64 Scope:link
                  UP BROADCAST RUNNIN MULTICAST MTU:1500 METRIC:1
                  Rx packets:297 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1000
                 RX bytes:288692 (281.9 kib) TX bytes:492 (492.0 b)

lo             (im not gona finish because lo is my dial up connection that i never use)

---

### Post by oreb on 2007-06-01
OK, that looks normal.  Looks like I'm barking up the wrong tree.  I don't have your answer but I'll think about it.

---

### Post by FKi on 2007-06-01
thanks alot anyways, i apreciate the efforts

---

### Post by FKi on 2007-06-01
k if anyone knows the answer to either of the problems, i would apreciate it

---

