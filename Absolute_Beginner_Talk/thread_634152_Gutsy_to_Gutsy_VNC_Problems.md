---
title: "Gutsy to Gutsy VNC Problems"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mannequin on 2007-12-07
Hi everyone,

If this has been covered before, please direct to me the page / thread. I cannot find a solution via several searches. :)

Anyway, my problem is that I cannot connect two machines with Gutsy on them via VNC via the preinstalled routes. (Remote Desktop, tsclient)

My machine will always error out with:
```

$ vncviewer 192.168.xxx.xxx

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Fri Dec  7 16:02:24 2007
 CConn:       connected to host 192.168.xxx.xxx port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7

Fri Dec  7 16:02:25 2007
 CConnection: No matching security types
 main:        No matching security types
```If I try to connect to my machine via the other one, it works.

I installed Gutsy on my machine a few days after Gutsy was released. Gutsy was installed on the other machine just today. This is the first time since I installed Gutsy on my computer (and the other computer) that I've tried to use the VNC server / client. They are on the same network. (The other machine is my wife's computer.) They are both using the same wireless network. They are using the same version of vncviewer (and VNC server) that comes with Gutsy.

So... any help would be appreciated. If you need any more information, please ask.

Thanks!
-M.

---

### Post by lamalex on 2007-12-07
can you do a portscan on the machines that are refusing connections?
```
sudo nmap -p 5900 192.168.xxx.xxx
```
You might need to install nmap too, I'm not sure if it's included by default. It's a good tool to have regardless.

---

### Post by mannequin on 2007-12-07
Thanks for replying so quickly. :)

Here's the nmap output as requested:
```
$ nmap -p 5900 192.168.xxx.xxx

Starting Nmap 4.20 ( http://insecure.org ) at 2007-12-07 16:51 GMT
Interesting ports on 192.168.xxx.xxx:
PORT     STATE SERVICE
5900/tcp open  vnc

Nmap finished: 1 IP address (1 host up) scanned in 0.375 seconds

```As far as I can see, it's an open port. :)

-M.

---

### Post by lamalex on 2007-12-07
Yeah, should be working... Is the other end asking for permission from the user to allow the connection? I initially had problems with gutsy asking for permission before it would connect. It doesn't request it on the client machine, it pops up a dialog on the host pc. Maybe that's the problem?

---

### Post by mannequin on 2007-12-07
I wish that I could say that a dialog popping up was the problem. But it isn't. My wife's computer rejects my connection almost immediately after I hit the "Connect" button. (Or the "Enter" key if I'm trying this via a terminal emulator.)

To make sure, though, I've disabled the confirmation and password entry checkboxes that are in vino-preferences. I'm still getting the same results. :(

-M.

---

### Post by Bealer on 2008-02-15
I'm getting the same problem as mentioned above.

Did you find a solution to the problem?

---

### Post by mannequin on 2008-02-16
Nope. Sorry. But, now I've gotten rid of the other computer, so I won't be able to test solutions.

-M.

---

