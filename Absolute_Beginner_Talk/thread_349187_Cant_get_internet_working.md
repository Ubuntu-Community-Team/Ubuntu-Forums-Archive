---
title: "Cant get internet working"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by dethredic on 2007-01-29
Ok i found an old laptop PII 128 mb ram and decided to put Ubuntu on it.

I have used Ubuntu on a virtual server before and liked it.

During the installation the internet auto setup did not work so i entered the info in the setup.

I apparently did not get the info correct.

I changed it so it was the same as my normal computer.

It can't seem to get it trying my router and normal ip in both options.

i hope you can help me resolve this, I can provide more information if needed

---

### Post by kb3hkg on 2007-01-30
in terminal send us the output of the command ifconfig

---

### Post by aidanh on 2007-01-30
also need help with internet/cable modem connection

here is my ifconfig 


lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436  Metric:1
       RX packets: 207 errors:0 dropped:0 overruns:0 frame:0
       Tx packets: 207 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes: 16560 (16.1 KiB) TX bytes: 16560 (16.1 KiB)





Aidan

---

### Post by dethredic on 2007-01-30
Here are the results


eth0   Link encap: Ethernet  HWaddr --:10A4:F4:FC:FA
         inet addr:24.57.211.255  Bcast 24.57.211.255  Mask:255.255.255.0
         intet6 addr: fe80::a4ff:fef4:fcfa/64 scope:link
         Up BROADCAST RUNNINGT MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frames:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0b)  TX bytes 468 (468.0b)
         Interrupt:3 Base address:0x300

lo       Link encap: Loopback
         inet addr 127.0.0.1   Mask:255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:216 errors:0 dropped:0 overruns:0 frame:0
         TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuuelen:0
         RX bytes:10800 (10.5 KiB)  TX bytes 10800 (10.5 KiB)

Hope it helps

---

### Post by kb3hkg on 2007-01-30
was this information all gathered automatically using dhcp or did you put it in staticly?

---

### Post by aidanh on 2007-01-30
i just typed it all in, found eth0 now so i must be getting close


eth0 Link encap: Ethernet HWaddr 00:20:18:56:88:42
     inet6 addr: fe80::220:18ff:fe56:8b42/64 Scope:Link
     UP BOARDCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets: 3497 errors:0 dropped:0 overruns:0 frame:0
     Tx packets: 25 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes: 216732 (211.1 Kib) TX bytes: 4194 (4.0 Mib)
     Interrupt:11 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets: 13192 errors:0 dropped:0 overruns:0 frame:0
Tx packets: 13192 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 1195374 (1.1 Mib) TX bytes: 1195374 (1.1 Mib)

---

### Post by dethredic on 2007-01-30
> was this information all gathered automatically using dhcp or did you put it in staticly?

that info was put in by me. the dhcp didn't work on setup

---

### Post by kb3hkg on 2007-01-30
if you are in fact running dhcp but it didn't work on startup try running dhclient

---

### Post by dethredic on 2007-02-06
>  	if you are in fact running dhcp but it didn't work on startup try running dhclient

and if i don't think i am running dhcp?

---

### Post by dethredic on 2007-02-08
any other suggestions?

---

