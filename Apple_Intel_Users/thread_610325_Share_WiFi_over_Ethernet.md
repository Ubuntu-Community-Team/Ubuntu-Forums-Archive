---
title: "Share WiFi over Ethernet"
date: 2007-11-11
forum: Apple Intel Users
---

### Post by direct45 on 2007-11-11
Hey there,

I just put Gutsy on an old PC of mine which has no wifi card and lives in a room far away from my router.  Too far to run an ethernet cable.

I have a MacBook which connects via WiFi, and I'm trying to figure out if there's a way for me to share my laptop internet connection with this PC by plugging an ethernet cable between the two.  In other words:

Wifi > Macbook > Ethernet > PC = Internet for PC

Is there a way to do this?

Much appreciated.

---

### Post by mcallenSchmee on 2007-11-11
This is possible. I think you just go to one of the networking menus on the mac and choose share internet connection, then choose -over ethernet.

---

### Post by cyberdork33 on 2007-11-11
should be easily doable in OSX, although you might need a crossover cable to connect the two machines like that.

---

### Post by david_edmundson on 2007-11-12
Don't encourage people to use Mac OS X on the Ubuntu Forums.

Set up the wifi
Set up the ethernet

(you will probably need to do the ethernet manually as there is no "server" giving out IP addresses)
on the macbook run
"sudo ifconfig eth0 up"
"sudo ifconfig eth0 192.168.1.1"
(and then on the windows PC set the ethernet address to 192.168.1.2 )

You can choose different IP's. 

run in a terminal
"sudo su" (to log you in as root)
and then
"echo 1 > /proc/sys/net/ipv4/ip_forward"

Your Macbook will now start acting like a router.

---

### Post by cyberdork33 on 2007-11-12
> **david_edmundson said:**
> Don't encourage people to use Mac OS X on the Ubuntu Forums.
He never said the Mac had Linux on it, but that the other machine did. Get over it.

---

### Post by direct45 on 2007-11-12
That's great... thanks all!  Stupidly simple.  

Although, I'm not exactly sure what I did to promote OSX use.  Or why that should matter in the slightest.  But whatever...  I'm excited to begin getting into the world of Linux.

---

### Post by david_edmundson on 2007-11-12
cyberdork33:

Sorry I didn't mean to sound like I was having a go at you. Wasn't intended as such.

---

