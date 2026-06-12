---
title: "ubuntu auto logs itself out"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-02-11
Hi
Ubuntu logs itself out recently without me asking it to. It happens seemingly randomly when i minimise a window. All that happens is that i lose whatever i was doing and have to go back in again, any ideas?

---

### Post by jan quark on 2008-02-11
do you have installed something "special" in the last days?
compiz?

what are your specs?

anything unusual in the logs?
system > administration > system log

---

### Post by ukripper on 2008-02-11
can you post output of the follwing command when it logs off again

```
tail -f /var/log/messages
```

---

### Post by Falc7 on 2008-02-11
nothing that comes to mind

specs
intel t7200 core 2
2gb ram
nvideao geforce go 7600

logs show this:
Feb 10 11:56:26 wer-laptop syslogd 1.4.1#21ubuntu3: restart.
Feb 10 12:10:03 wer-laptop -- MARK --

yep i use compiz


edit:
@ukripper, okay i'll do that

---

### Post by Falc7 on 2008-02-18
wer@wer-laptop:~$ tail -f /var/log/messages
Feb 18 21:11:41 wer-laptop -- MARK --
Feb 18 21:31:41 wer-laptop -- MARK --
Feb 18 21:51:41 wer-laptop -- MARK --
Feb 18 22:11:41 wer-laptop -- MARK --
Feb 18 22:31:41 wer-laptop -- MARK --
Feb 18 22:51:41 wer-laptop -- MARK --
Feb 18 23:11:41 wer-laptop -- MARK --
Feb 18 23:31:41 wer-laptop -- MARK --
Feb 18 23:48:42 wer-laptop Failed to open the panel socket 
Feb 18 23:48:43 wer-laptop Failed to open the panel socket 


It happened again, i just minimised a amsn convo and it logged out

---

### Post by Falc7 on 2008-02-19
anyone?

---

### Post by ukripper on 2008-02-20
Looks like problem is  with panels.

Try reinstalling Nautilus. Run following in terminal
```
sudo aptitude update && sudo aptitude reinstall nautilus && sudo aptitude dist-upgrade
```

---

### Post by Falc7 on 2008-02-20
thanks, i hope this works

---

### Post by Falc7 on 2008-02-21
It happened again, anything else i can try?

---

### Post by Falc7 on 2008-03-03
Mar  3 17:03:43 wer-laptop kernel: [16656.972000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=91.68.17.109 DST=192.168.0.4 LEN=294 TOS=0x00 PREC=0x00 TTL=52 ID=49018 PROTO=UDP SPT=8746 DPT=6881 LEN=274 
Mar  3 17:03:55 wer-laptop kernel: [16669.584000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=76.170.238.255 DST=192.168.0.4 LEN=294 TOS=0x00 PREC=0x00 TTL=100 ID=43582 PROTO=UDP SPT=33279 DPT=6881 LEN=274 
Mar  3 17:08:22 wer-laptop kernel: [16935.892000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=212.40.88.129 DST=192.168.0.4 LEN=1448 TOS=0x00 PREC=0x00 TTL=108 ID=31186 DF PROTO=TCP SPT=64139 DPT=48662 WINDOW=65149 RES=0x00 ACK URGP=0 
Mar  3 17:10:23 wer-laptop kernel: [17057.780000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=212.40.88.129 DST=192.168.0.4 LEN=1448 TOS=0x00 PREC=0x00 TTL=108 ID=35020 DF PROTO=TCP SPT=64139 DPT=48662 WINDOW=65149 RES=0x00 ACK URGP=0 
Mar  3 17:11:21 wer-laptop kernel: [17115.392000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=124.78.163.5 DST=192.168.0.4 LEN=294 TOS=0x08 PREC=0x20 TTL=42 ID=49967 PROTO=UDP SPT=21400 DPT=6881 LEN=274 
Mar  3 17:11:49 wer-laptop kernel: [17143.584000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=89.128.162.115 DST=192.168.0.4 LEN=294 TOS=0x00 PREC=0x00 TTL=113 ID=27931 PROTO=UDP SPT=35041 DPT=6881 LEN=274 
Mar  3 17:12:07 wer-laptop kernel: [17161.600000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=98.204.11.223 DST=192.168.0.4 LEN=95 TOS=0x00 PREC=0x00 TTL=106 ID=8661 PROTO=UDP SPT=41165 DPT=6881 LEN=75 
Mar  3 17:12:20 wer-laptop kernel: [17174.608000] Inbound IN=eth1 OUT= MAC=00:19:d2:d1:7a:fe:00:1b:2f:95:4f:68:08:00 SRC=212.40.88.129 DST=192.168.0.4 LEN=1448 TOS=0x00 PREC=0x00 TTL=108 ID=38103 DF PROTO=TCP SPT=64139 DPT=48662 WINDOW=65149 RES=0x00 ACK URGP=0 
Mar  3 17:26:25 wer-laptop -- MARK --
Mar  3 17:39:41 wer-laptop Cleanup, done. Exitting... 

It happened again, this is the output this time

---

### Post by ukripper on 2008-03-04
You sure you don't have any shortcut key enabled which when pressed is logging you out?

Check this [https://help.ubuntu.com/7.10/user-guide/C/keyboard-skills.html](https://help.ubuntu.com/7.10/user-guide/C/keyboard-skills.html)

---

### Post by Falc7 on 2008-03-04
Yes i am quite sure, i wouldn't even know how to set that up (is there an easy way to check if i have any custom shortcuts set up?), and plus most of the time when it happens i am not pressing anything on the keyboard, just minimising something with the mouse, usually.

---

