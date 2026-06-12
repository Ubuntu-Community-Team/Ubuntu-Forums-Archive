---
title: "Remote Desktop / Internet only works when Firestarter is turned off (VPN)"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by HautingLu on 2007-08-06
Hi,

I've been able to VPN into work with some tweaking of the user-pre file. Now I can ping my XP PC, but can't remote desktop or surf the web (while I'm VPN'ed in). But if I stop the firewall, then everything works...internet, remote desktop. 

But I can't figure out what's missing in Firestarter. I added my XP's IP into a rule for inbound. Outbound is permissive. Is it possible there is another machine in between us that needs a rule in Firestarter? 

Also, is there any harm in stopping the firewall temporarily while vpn'ing into work?


Thanks!

This and tweaking with dyn dns are the last things holding me back from blowing away Vista :guitar:

---

### Post by moore.bryan on 2007-08-06
*if your work is anything like mine, there is, at least, another machine in-between...*

---

### Post by HautingLu on 2007-08-06
> **moore.bryan said:**
> *if your work is anything like mine, there is, at least, another machine in-between...*

Was this machine obvious from logs and you just added a rule for it? Give me a hint \\:D/

---

### Post by moore.bryan on 2007-08-06
*unfortunately, i was never able to vpn into it at all... blocked all attempts from linux comps... when i asked our "tech guru," he just told me linux is completely unstable and unsafe, so our vpn doesn't allow computers running linux to connect.*

---

### Post by HautingLu on 2007-08-06
> **moore.bryan said:**
> *unfortunately, i was never able to vpn into it at all... blocked all attempts from linux comps... when i asked our "tech guru," he just told me linux is completely unstable and unsafe, so our vpn doesn't allow computers running linux to connect.*

Thanks. I guess I'll stick to asking the Linux guru(s) that sit next to me.

---

### Post by moore.bryan on 2007-08-06
*i wish i had that... :-(*

---

### Post by bodhi.zazen on 2007-08-06
Just checking, are you sure you have the correct IP (you know not to use the IP on the LAN) ?

This may help as well : [http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

---

### Post by HautingLu on 2007-08-06
> **bodhi.zazen said:**
> Just checking, are you sure you have the correct IP (you know not to use the IP on the LAN) ?

This may help as well : [http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

Yup I think the IP's are good to go. I think I've narrowed it down:

-Everything works ok with the firewall off (Firestarter)
-The new ppp0 connection seems to have no traffic with the firewall on. Out/In are only a few Kb's.
-Logs repeat with firewall on:

Aug  6 22:35:12 ubuntu kernel: [57846.270120] Unknown InputIN=ppp0 OUT= MAC= SRC=**ip1** DST=**ip2** LEN=1412 TOS=0x00 PREC=0x00 TTL=43 ID=37336 PROTO=TCP SPT=80 DPT=48193 WINDOW=65535 RES=0x00 ACK URGP=0

Where **IP1** is some unknown IP and **IP2** is the IP given to my pp0. Not sure if that makes any sense, but in any case I added both to allowed inbound connections.

Am I still missing something?

Thanks.

---

