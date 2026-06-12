---
title: "strange dmesg output"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by duruttye on 2008-03-18
Hey, any ideas what this could be?

[HTML][ 3562.306232] Inbound IN=eth0 OUT= MAC=00:1c:23:ad:06:23:00:90:d0:1a:47:75:08:00 SRC=77.125.8.107 DST=192.168.1.65 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=41284 DF PROTO=TCP SPT=4210 DPT=18106 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 3563.953324] Inbound IN=eth0 OUT= MAC=00:1c:23:ad:06:23:00:90:d0:1a:47:75:08:00 SRC=77.125.8.107 DST=192.168.1.65 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=41524 DF PROTO=TCP SPT=4210 DPT=18106 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 3566.494320] Inbound IN=eth0 OUT= MAC=00:1c:23:ad:06:23:00:90:d0:1a:47:75:08:00 SRC=77.125.8.107 DST=192.168.1.65 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=41988 DF PROTO=TCP SPT=4210 DPT=18106 WINDOW=65535 RES=0x00 SYN URGP=0[/HTML]

Found it in dmesg output, very much of it, never seen before.
I think someone trying to access my 18106 port from that IP address, eve though that port is blocked from firestarter.

Any ideas?
thanx

---

### Post by bswilson on 2008-03-19
Nothing strange about it at all.  As you know, **dmesg** writes kernel messages to standard output.  This is just communication flows that are blocked by **ipchains** while your system is booting.  Nothing to be concerned about.

---

### Post by duruttye on 2008-03-19
Hey!
I wasn't really concerned, just wanted to know what's happening.
I know that my pc isn't an easy task for whoever wants to hack into it, so they just better move on and find some welcoming windoz machines, there are many of them out there:)
Whenever I find out something interesting  about ubuntu I'm glad!

So thanx.

---

