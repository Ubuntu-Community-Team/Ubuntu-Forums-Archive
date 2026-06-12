---
title: "Problem connecting to the Internet via dialup"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Rey Morata on 2008-01-09
Hello, I'm a new user of Ubuntu Gutsy. All installed well, but I need to have updates. I cannot download any updates because of these lone
issue I encountered everytime I connect to the Internet via dial-up 
modem. Here's the ever recurring problem using wvdial: 

"WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT10121
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT10121
WvDial Modem<*1>: CONNECT 460800
WvDial Modem<*1>: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@PLDT@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
WvDial Modem<*1>:  WARNING !!! UNAUTHORIZED ACCESS TO THIS FACILITY IS
WvDial Modem<*1>:        PROHIBITED BY LAW. IF YOU HAVE ACCESSED THIS SYSTEM BY
WvDial Modem<*1>:        MISTAKE, YOU MAY DISCONNECT NOW. THANK YOU
WvDial Modem<*1>: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@IP-DIAL@@@@@@@@@@@@@@@@@@@@@@@@@@@ 
WvDial Modem<*1>: User Access Verification
WvDial Modem<*1>: Username: 
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Wed Jan  2 12:14:30 2008
WvDial<Notice>: Pid of pppd: 6413
WvDial<*1>: Using interface ppp0
WvDial<*1>: Disconnecting at Wed Jan  2 12:14:34 2008
WvDial<*1>: The PPP daemon has died: Authentication error.
WvDial<*1>: We failed to authenticate ourselves to the peer.
WvDial<*1>: Maybe bad account or password? (exit code = 19)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 19)"

Any help would be greatly appreciated.  Thanks.

=============
Processor = P4 Intel 64-bit 3Ghz (single core)
Memory = 1 Gb DDR
VPU = ATI Radeon 9250 Game FX
Modem = Conexant 56K
HDDs = 80Gb SATA (Windows)/ 80Gb ATA (Ubuntu)
Dual Boot = Windows XP x64/ Ubuntu 7.10 PC-64-bit

---

### Post by shareMenaPeace on 2008-01-09
Hi, 
did you tried using no password?
This is some sort of authentication (login) issue.
You can reconfigure the pppoe setup with

```
pppoeconf 

```
Just follow the default settings ...

Cheers

---

### Post by Rey Morata on 2008-01-10
Thanks for your immediate concern.

Fortunately, last night, my modem successfully connected to the Internet without 
changing any, just using the wvdial command.

My problem now is, it still can't download any Ubuntu updates after issuing this
command: sudo apt-get update

Thanks again.

---

