---
title: "help in internet connection using cable modemD"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by listen on 2005-09-21
Hi!

I have downloaded and installed Ubuntu 5.10 and am trying to connect the cable modem (motorola surfboard SB51001) thru the PCI ethernet card.

Based on help from another post, i have keyed in certain commands to find out my problem.....the results are as follows:-


mark@mark:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:26:8D:D7:52
          inet6 addr: fe80::2c0:26ff:fe8d:d752/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:459066 (448.3 KiB)  TX bytes:2430 (2.3 KiB)
          Interrupt:10 Base address:0x9400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1439746 (1.3 MiB)  TX bytes:1439746 (1.3 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

mark@mark:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
mark@mark:~$ ping 216.109.117.108
connect: Network is unreachable
mark@mark:~$ dig ubuntu.com

; <<>> DiG 9.3.1 <<>> ubuntu.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

I have also checked thru the "Systems->administration->networking" and under the "connections" tab, there are 2 entries:-
Ethernet connection - the interface eth0 is active
Modem connection - the interface ppp0 is not configured



pls give some advice on what should i do next...thanks in advance..

my com specs are:-
Motherboard: Aopen AX6BC Pro Pentium II 100 Mhz BIOS ver 1.6
Processor: Intel Celeron 400 Mhz
Ram : PC100 SDRAM 256MB
Graphics card: 16 MB Riva TNT2 Creative
Sound card: Vibra128 Creative
Harddisk: 8.5Gb Quantum
Casing : 230 W ATX 
CD Drives: 1 X TDK CD-RW 40/12/48 and 1 X CD-ROM
Floppy Drive: 1
Ethernet card: 1 X PCI

---

### Post by Mr. Electric Wizard on 2005-09-21
Looks to me like your NIC is not working.
What kind of NIC is it?

---

### Post by listen on 2005-09-21
Thanks for your help...
its says on the card Prolink PFE-100TX....
when i connect the cable....the yellow and green....flashes.....
i also did a reboot after connecting the cable...

---

### Post by SilentCacophony on 2005-09-21
While I'm not terribly proficient with network setup, I did notice something missing in your setup. Here is mine, with the difference in bold:


brian@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:88:46:6E:15
          i**net addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0**
          inet6 addr: fe80::20d:88ff:fe46:6e15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9548448 (9.1 MiB)  TX bytes:832769 (813.2 KiB)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2542080 (2.4 MiB)  TX bytes:2542080 (2.4 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Mine is set up through a router, and so probably has a different ip than yours normally would. If I run a *netstat -nr*, it shows this:

```

brian@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0
```

Yours should look similar, but probably with 192.168.0.X. If it doesn't, have a look at [this](http://ubuntuforums.org/showthread.php?t=25557) thread for more info on how to set up a gateway.

---

### Post by listen on 2005-09-21
Thank SilentCacophony and Electric Wizard,

I think both of you are right...my NIC doesnt seemed to be configured correctly or at all.....wondered why did the System->administration->networking->connections tab indicated that teh ethernet connection is active...

anyway ...i read the link on the Howto-basic networking and troubleshooting....
gives an insight on my problem....really...but i still dont know what steps to do to 
1. check my NIC configuration...
2. configure it...

anyone pls...thanks in advance...

---

### Post by listen on 2005-09-21
Thank you  SilentCacophony and Electric Wizard,

the results for netstat -nr and route are the same ......nothing....except the headers....

there was also an error during booting after network configuration...someting mentioning about..."error failure in name resolution..."..must be linked to this problem...also...

I think both of you are right...my NIC doesnt seemed to be configured correctly or at all.....wondered why did the System->administration->networking->connections tab indicated that teh ethernet connection is active...

anyway ...i read the link on the Howto-basic networking and troubleshooting....
gives an insight on my problem....really...but i still dont know what steps to do to 
1. check my NIC configuration...
2. configure it...

anyone pls...thanks in advance...

---

### Post by SilentCacophony on 2005-09-21
Just wondering, when you said you did a reboot, did you power both the modem and the computer down, then power the modem up first (let it finish it's bootup, usually a couple of minutes,) then power up the computer? That can often be needed if there is a network problem, and has solved mine before.

If not, the ip of the modem with a single computer > modem setup would *usually* be 192.168.0.1, and you could try:

route add default gw 192.168.0.1

I don't know if that would work, but it was outlined in that link I posted before. I'd try the cold boot first.

---

### Post by listen on 2005-09-22
Dear SilentCacophony,

You are my angel... its works!!! i didnt knew that i had to repower the cable modem....didnt crossed my mind...i thot for cable modems...they are a constant source of signals...so no need to repower...infact, i was pluging in and out between my notebook and desktop....so i posted using the laptop and had to replug it back to the desktop and and rebooted the linux OS...
vice-versa, now when i replug it back to the notebook...the internet doesnt seemed to be working....reinitializing the modem did the job...
i guess there is some initializing with the comp needs to be done ...

ok mission accomplished...thank you so much..  :) 

sincerely 
listen

---

