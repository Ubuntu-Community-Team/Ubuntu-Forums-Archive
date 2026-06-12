---
title: "Dell Inspiron + Ubuntu + Belkin problems"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by sanderella on 2007-02-27
I recently bought myself a Dell Inspiron 1300. I took
it to the Hants LUG at Souhampton a couple of months ago, and
someone kindly installed Ubuntu Dapper for me. While
at the LUG the wireless system worked perfectly and I
had no problems getting online. However, since I got
home, I cannot configure the system to get online with
this laptop and my Belkin. 

At home I have a Belkin G54 modem with wireless
router. My desktop Ubuntu computer picked it up and
connected automatically. When the laptop is running
Windows it works perfectly. When I try to get online
with Ubuntu, it just doesn't work at all now matter
how I try.

Why can I pick up the signal at the LUG yet
not at home? Why can Windows pick up the signal on the
laptop, but Ubuntu can't find it? Can someone help me please? :(

---

### Post by bigken on 2007-02-27
go to system administration networking and double click on the wireless conection add your essid and wep if you have any

---

### Post by sanderella on 2007-02-27
Nope, still not working :(

---

### Post by bigken on 2007-02-27
is it showing any kind of signal right click on the task bar and add network manager

---

### Post by bigken on 2007-02-27
in a terminal type this **ifconfig **and post it back

---

### Post by sanderella on 2007-02-27
The wireless isn't working in Windows now. I think this is a Windows/Dell/Linux conflict problem. I'm going to have to take it back to Dell, I think.

Thanks, Sandra:(

---

### Post by sanderella on 2007-03-14
Well I found out the answer to my questions on the Ubuntu hardwear support page.

"Ships with Celeron model [WWW] Inspiron 1300. Tried ndiswrapper and firmware methods forum [WWW] thread. lspci reports: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). Card starts up but cannot find any way to connect to network with dapper"

So there it is: my wireless card won't work with dapper. Does anyone know if the Dell Wireless 1370WLAN mini-pci card works with edgy? Or am I going to have to change my distro?

I'm grateful for any comments.

---

### Post by sanderella on 2007-03-14
It's ok guys, I just found the answer! :)

---

