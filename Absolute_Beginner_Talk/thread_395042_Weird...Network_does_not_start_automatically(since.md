---
title: "Weird...Network does not start automatically(since around weekend)"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by almacen on 2007-03-27
Hi, There are a few of us who seem to be having this problem. Since around the weekend, our network connection has gone weird. When we turn on the computer, we do not have a connection. (me,mikeSz,Ajex, and I think a few more)

if I go to system->administration->Networking, it says say "eth0 is active". If I "deactivate" it and again "Activate" it the problem goes away....But why is it failing to start automatically at the start?

I have been on ubuntu 6.06 a couple of months now, and haven't installed anything new on it over the past few weeks, apart from ubuntu updates...

Any help greatly appriciated!

---

### Post by MikeSz on 2007-03-27
cheers!  yep, this includes me too.  See my thread about weird internet problems.

---

### Post by mkjarema on 2007-03-27
> **MikeSz said:**
> cheers!  yep, this includes me too.  See my thread about weird internet problems.

Could you put the link in this thread?  Thanks!

---

### Post by almacen on 2007-03-27
> **mkjarema said:**
> Could you put the link in this thread?  Thanks!
here's the original thread:
[http://www.ubuntuforums.org/showthread.php?t=394804](http://www.ubuntuforums.org/showthread.php?t=394804)
Thanks for looking!

---

### Post by locke.dragon on 2007-03-27
since it's dual-boot, wireless sometimes gets shut off on laptops after booting into windows (at least on mine it does). all you need to do do fix the problem is...

1. boot back into windows
2. turn on wireless via fn + wireless (f2 on my box)
3. shut down windows
4. boot into ubuntu

this works every time on my machine. hope that helps!

---

### Post by MikeSz on 2007-03-28
I dont have wireless so doesnt that make a difference?

---

### Post by locke.dragon on 2007-03-28
is it a wired network?  like...  your computer is connected to one or more other computers with a cable?

---

### Post by MikeSz on 2007-03-28
I think me and the others are mainly talking about the internet - sorry if thats unclear.  My computer isnt networked, but we're just wondering if any of the updates released at the weekend have caused anyone else any problems as a few of us seem to have lost internet connectinos and are experiencing those difficulties outlined since this weekend.

---

### Post by almacen on 2007-03-28
> **locke.dragon said:**
> is it a wired network?  like...  your computer is connected to one or more other computers with a cable?

Mine is a university wired network.....

---

### Post by MikeSz on 2007-03-30
Ok - sorry guys but this is still causing me some confusion.  when I log into Ubuntu (on either of my logon's) I cannot connect to the internet.  This happens every time and although it sometimes resolves itself, often it doesnt.  I have however tried the suggestions left on my previous thread and typed "sudo dhclient" into terminal and after I do that, my internet works again.  If it helps, heres what I typically get in terminal...

bespin@mike-desktop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.90 -- renewal in 32622 seconds.
bespin@mike-desktop:~$


Anyone know what is causing this and why I have to keep doing this to get my internet working?  Shouldnt it just 'work' automatically everytime I log in without me having to faff like this?  I know its a small faff but there must be a reason why its doing it?

---

### Post by MikeSz on 2007-03-31
Ok, this is getting a little dodgy now - Im still suffering the problem, heres the latest output from teminal....

bespin@mike-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.90 -- renewal in 40190 seconds.
bespin@mike-desktop:~$

Also, I checked my parents machine today which also has 6.06 dapper on it and they have just had EXACTLY THE SAME problem as I have.  sudo dhclient fixes it but can anyone please help with this?  Its obviously something in an update.  Can anyone help fix it?

---

### Post by MikeSz on 2007-04-01
Can anyone please help with this?

---

### Post by almacen on 2007-04-04
Mine has started working normally again (There were some Ubuntu updates yesterday)..... how is yours looking MikeSz?

---

