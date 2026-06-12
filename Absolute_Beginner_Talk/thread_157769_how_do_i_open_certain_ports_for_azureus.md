---
title: "how do i open certain ports for azureus"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-04-09
is there a way to open certain ports so that i can use azureus bittorrent cliet?

Is there a way to check which ports are open?

---

### Post by joshrobinson on 2006-04-09
[QUOTE=racermike1967]is there a way to open certain ports so that i can use azureus bittorrent cliet?

Is there a way to check which ports are open?[/QUOTE]

are you running firestarter?
i just opened the ports on my router 6880-6889 as BOTH udp and TCP
and then 6999 as BOTH udp and TCP
and azureus connects fine for me

run nat firewall test in az. then put in the port you wana use and click test.. if it says OK just hit apply and your good to go

---

### Post by racermike1967 on 2006-04-09
i am actually connecting to the internet from a dorm room and i never downloaded firestarter so i don't think i have it.  i tried several port numbers in the nat firewall test but nothing was good.

---

### Post by Sutekh on 2006-04-09
You're most likely connecting through a router for the entire dorm.  You'll need to configure the router to allow connections through ports 6880-6889 to the IP of your computer.

Now if you can convince who ever is responsible for the router to set that up for you, you will be sweet.

---

### Post by joshrobinson on 2006-04-09
[QUOTE=Sutekh]You're most likely connecting through a router for the entire dorm.  You'll need to configure the router to allow connections through ports 6880-6889 to the IP of your computer.

Now if you can convince who ever is responsible for the router to set that up for you, you will be sweet.[/QUOTE]

yeah as said above its out of your hands now.. you have to talk to the sysadmin to help you out.. maybe upnp will work? try turning that on in az. under the options then plugins menu if its not already on

---

### Post by xmux on 2006-05-28
Hey i have the same Problem, but our Admin doesn't understand well about Computers, she wanted to get some points only... anyway ist there some programms for to look and open some ports for myself???

---

