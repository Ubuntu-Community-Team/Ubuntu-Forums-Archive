---
title: "[SOLVED] tsclient issue"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-04-07
tsclient hangs after a few minutes, no errors given it just disconnects.  

IBM t60 laptop

---

### Post by dstew on 2008-04-08
Do you see any error messages in dmesg? (Enter dmesg on the command line after it disconnects). The messages might be for rdesktop, because TSClient is just a graphical front-end for that program. Also, you might need to install a VPN program. Check in Synaptic. I think the Cisco program might be in the Universe repository (sorry, not at my Linux machine to check).

---

### Post by herbster on 2008-04-08
Can you be more specific? Also, run the program from the terminal and paste the output if any when it hangs.

Are you trying to connect to a networked Windows machine? Is it XP/2000/Vista/etc?

---

### Post by TechDragon on 2008-04-09
Hello,

This is happening every few minutes, it is getting very frustrating.  It is Ubuntu to WindowsXP, the windowsXP box is inside of a domain at work.  I can connect windowsXP to WIndowsXP and be connected for hours but Ubuntu to WindowsXP only lasts a few minutes.  

I am using TSclient or Gnome-rdp both do the exact same thing.

Attached are some screenshots and the code that was requested.

> 8:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=46536 PROTO=TCP SPT=80 DPT=2194 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=127 ID=19283 PROTO=UDP SPT=137 DPT=137 LEN=64 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=77 TOS=0x00 PREC=0x00 TTL=127 ID=19284 PROTO=UDP SPT=53 DPT=1026 LEN=57 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=127 ID=19336 PROTO=UDP SPT=137 DPT=137 LEN=64 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=77 TOS=0x00 PREC=0x00 TTL=127 ID=19349 PROTO=UDP SPT=53 DPT=1026 LEN=57 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=77 TOS=0x00 PREC=0x00 TTL=127 ID=19416 PROTO=UDP SPT=53 DPT=1026 LEN=57 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=196 TOS=0x00 PREC=0x00 TTL=127 ID=22308 PROTO=UDP SPT=53 DPT=2207 LEN=176 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=90 TOS=0x00 PREC=0x00 TTL=127 ID=24061 PROTO=UDP SPT=137 DPT=137 LEN=70 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=77 TOS=0x00 PREC=0x00 TTL=127 ID=27919 PROTO=UDP SPT=53 DPT=1026 LEN=57 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.248.183 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=28774 PROTO=TCP SPT=80 DPT=2459 WINDOW=16384 RES=0x00 ACK SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.248.183 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=29359 PROTO=TCP SPT=80 DPT=2459 WINDOW=16384 RES=0x00 ACK SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.248.183 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=30698 PROTO=TCP SPT=80 DPT=2459 WINDOW=16384 RES=0x00 ACK SYN URGP=0 OPT (020405B401010402) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=3517 PROTO=TCP SPT=80 DPT=2471 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=127 ID=40792 PROTO=UDP SPT=137 DPT=137 LEN=64 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=77 TOS=0x00 PREC=0x00 TTL=127 ID=51870 PROTO=UDP SPT=53 DPT=1026 LEN=57 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=1857 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=56588 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=1857 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=56588 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=28240 PROTO=TCP SPT=80 DPT=2685 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=33496 PROTO=TCP SPT=80 DPT=2685 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=42913 PROTO=TCP SPT=80 DPT=2691 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=43222 PROTO=TCP SPT=80 DPT=2691 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=29574 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.4.5 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=123 ID=9654 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=29707 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=29739 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.4.5 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=123 ID=10284 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=47772 PROTO=TCP SPT=80 DPT=2691 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=30639 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=52036 PROTO=TCP SPT=80 DPT=2691 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=31813 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=32798 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=63877 PROTO=TCP SPT=80 DPT=2691 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=5657 PROTO=TCP SPT=80 DPT=2697 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=10307 PROTO=TCP SPT=80 DPT=2697 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=21512 PROTO=TCP SPT=80 DPT=2697 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=51921 PROTO=UDP SPT=53 DPT=1026 LEN=65 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=2850 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=3160 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=3260 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=3471 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=5101 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=9081 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=15627 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.1.61 DST=10.12.12.40 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=21127 PROTO=TCP SPT=80 DPT=2972 WINDOW=65535 RES=0x00 ACK SYN URGP=0 OPT (020405B4) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=18995 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=59148 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=18995 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=59148 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=32224 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=59660 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=32224 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=59660 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=25698 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=60428 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=25698 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=60428 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.248.183 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=3774 PROTO=TCP SPT=80 DPT=3332 WINDOW=16384 RES=0x00 ACK SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.248.183 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=14002 PROTO=TCP SPT=80 DPT=3332 WINDOW=16384 RES=0x00 ACK SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.248.183 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=1515 PROTO=TCP SPT=80 DPT=3332 WINDOW=16384 RES=0x00 ACK SYN URGP=0 OPT (020405B401010402) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=77 TOS=0x00 PREC=0x00 TTL=127 ID=4180 PROTO=UDP SPT=53 DPT=1026 LEN=57 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=21998 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=62220 
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=21998 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=62220 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=29469 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.4.5 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=123 ID=52050 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=29606 PROTO=UDP SPT=53 DPT=1855 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=29657 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.4.5 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=123 ID=52644 PROTO=UDP SPT=53 DPT=1855 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=33031 PROTO=UDP SPT=53 DPT=1855 LEN=65 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=34007 PROTO=UDP SPT=53 DPT=1026 LEN=65 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=35661 PROTO=UDP SPT=53 DPT=1026 LEN=65 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.61 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=11388 DF PROTO=TCP SPT=1480 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B401010402) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.4.5 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=123 ID=3856 PROTO=UDP SPT=137 DPT=137 LEN=64 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.61 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=11992 DF PROTO=TCP SPT=1477 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.61 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=11998 DF PROTO=TCP SPT=1480 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B401010402) 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.61 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=13792 DF PROTO=TCP SPT=1477 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.61 DST=10.12.12.40 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=13793 DF PROTO=TCP SPT=1480 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B401010402) 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=94 TOS=0x00 PREC=0x00 TTL=127 ID=38854 PROTO=UDP SPT=53 DPT=1026 LEN=74 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=94 TOS=0x00 PREC=0x00 TTL=127 ID=39066 PROTO=UDP SPT=53 DPT=1026 LEN=74 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=94 TOS=0x00 PREC=0x00 TTL=127 ID=41976 PROTO=UDP SPT=53 DPT=1026 LEN=74 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.6.4.5 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=123 ID=18965 PROTO=UDP SPT=137 DPT=137 LEN=64 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=127 ID=44560 PROTO=UDP SPT=137 DPT=137 LEN=64 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=127 ID=46988 PROTO=UDP SPT=137 DPT=137 LEN=64 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=94 TOS=0x00 PREC=0x00 TTL=127 ID=48771 PROTO=UDP SPT=53 DPT=1026 LEN=74 


---

### Post by TechDragon on 2008-04-10
still doing it,

> SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=84 TOS=0x00 PREC=0x00 TTL=127 ID=46588 PROTO=UDP SPT=137 DPT=137 LEN=64 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC=00:1a:6b:67:d3:d5:00:0a:b8:8c:3a:44:08:00 SRC=10.12.3.1 DST=10.12.12.40 LEN=85 TOS=0x00 PREC=0x00 TTL=127 ID=51258 PROTO=UDP SPT=53 DPT=1026 LEN=65 
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
martian source 10.12.12.255 from 10.12.12.40, on dev eth0
ll header: ff:ff:ff:ff:ff:ff:00:1e:4f:50:5c:83:08:00
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=10.12.12.40 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 


---

### Post by herbster on 2008-04-10
[http://forum.soft32.com/linux2/Weird-Log-Messages-ftopict33231.html](http://forum.soft32.com/linux2/Weird-Log-Messages-ftopict33231.html)

See if that helps.

---

### Post by TechDragon on 2008-04-10
hmm, not really, no solution was found on the page.

---

### Post by herbster on 2008-04-11
What do you get in the terminal trying the basic approach:

```
rdesktop -u username -p password -g 1024x768 192.168.x.x
```

Of course user/pass replace with yours, and the IP as well.

---

### Post by TechDragon on 2008-04-13
I believe I have figured it out.  It appears to be a firewall issue.  I installed firestarter right after installing ubuntu, after running nexus3 against the unprotected ubuntu.  It failed the nexus3 test, or I should say it was pretty wide open.  I installed firestarter and it sealed it shut.  I removed firestarter and the problem persisted.  I reinstalled ubuntu and left firestarter out and my issues have slowed considerably.

---

