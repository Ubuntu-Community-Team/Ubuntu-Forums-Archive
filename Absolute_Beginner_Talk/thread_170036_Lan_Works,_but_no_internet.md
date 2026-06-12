---
title: "Lan Works, but no internet"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by wolflord on 2006-05-03
Hi all !

I am a newbie on Ubuntu. i have just installed Ubuntu 5.04 and is already stuck.

I currently have few home pc's running on Windows XP. I am currently using the internet on these pc's via a 4 port WAN router and a 8 port switch.
The network is all in working order and that includes the Ubuntu pc. I can access all the windows based pc's from the Ubuntu pc and visa versa. (All default settings, automatic ip settings etc.) Yet for some reason I cannot surf the net. 
All the windows based systems connect with no problems and I also know the that the hardware on the recently installed Ubuntu pc is in wokring order. It used to run windows XP with no problems.

I ran the "sudo PPPOECONF" command. I get a message that reads that it found ethernet device eth0. when I do a scan I get the following error message ppoe:access concentrator on eth0 is mtu of 1320 - should be 1500"
Could that be the problem or do I need to look somewhere else. If it is the problem how would I go about changing it or is there any other solution. ?

Any help would be much appreciated.

Thank you !

---

### Post by nanotube on 2006-05-03
well, first of all, you should not really be installing 5.04, 5.10 is the latest release, and 6.06 is around the corner. 
so if you can, get 5.10 and install that, and maybe your problems will go away. :)

---

### Post by wolflord on 2006-05-04
Thanks 4 the advice nanotube. Unfotunately I am only able to get my hands on 5.10 during the weekend. Hopefully that solves the problem. If not, back to the drawing board. :)

---

### Post by nanotube on 2006-05-04
[QUOTE=wolflord]Thanks 4 the advice nanotube. Unfotunately I am only able to get my hands on 5.10 during the weekend. Hopefully that solves the problem. If not, back to the drawing board. :)[/QUOTE]
ok good luck. post back if you run into problems.

---

### Post by uteck on 2006-05-05
If the Ubuntu machine can see all the computers on the LAN, then do you need to run the ppoe software?  If you have a DSL router that everything is hooked up to and providing IP address's, then the machine should get an address and just work automatically.

---

