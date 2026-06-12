---
title: "DSL onlyworks to get to UBUNTU.com"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by riverpaddler on 2006-09-27
Okay, I'm really a beginner. Just installed ubuntu 6.06 on this IBM Thinkpad. I have a DLink DWL Version C wireless card. I have connection... I think..???? I can connec to this website and no others. I can't get to google or any other places. Same thing happens witht he ethernet connection. What have I don't wrong?

Jacque

---

### Post by jd65pl on 2006-09-27
Try this to find out which network devices you have active and post the result back

```
ifconfig
```

You could also try this to see if you do have a connection

```
ping www.google.co.uk
``` 

Thanks

---

### Post by riverpaddler on 2006-09-27
gale@gale-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:BA:89:8F
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:feba:898f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:70 dropped:0 overruns:0 frame:70
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:2162 (2.1 KiB)  TX bytes:2092 (2.0 KiB)
          Interrupt:11 Memory:d0ba0000-d0bb0000

eth0      Link encap:Ethernet  HWaddr 00:03:47:B6:8E:DB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

gale@gale-laptop:~$
gale@gale-laptop:~$

I was able to ping [www.google.co.uk](www.google.co.uk) but not [www.google.com](www.google.com) I guess I can't get all the way to this forum with ubuntu. I am switching between a drive with xp installed and one with ubuntu. Maybe I just need a different wireless card but I hate to go out an buy one if it's not going to help.  The problem is the same with the ethernet connection.

---

### Post by jordanmthomas on 2006-09-27
May be a stretch, but try this:
In firefox, type about:config in the address bar
Search for ipv6 and enable it.

---

### Post by gn2 on 2006-09-27
Have you added the adaptor's MAC address to the router's allowed list?

Green indicator in the icon in the top right of the desktop?

Wlan activated correctly by Ubuntu?

SSID/WEP key entered correctly?

SPI Firewall issue?

Browser connection settings correct?

Wireless card inserted during install?

D-Link DWL??? Not all of them work, ACX100 chipset models seem OK. Mine's a DWL650+

When I installed Ubuntu I had connection difficulties which were only resolved by re-installing three (or so, I forget) times to get the installer to correctly configure the network settings.
If it fails to set up correctly during install, keep trying until it does.


Good luck...

---

### Post by NetworkGuy on 2006-09-27
This sounds like a DNS problem.  Respond to this with the output from ```
cat /etc/resolv.conf
```

---

### Post by enopepsoo on 2006-09-27
Did you configure your pppoe connection?:confused: 

:KS

---

### Post by GreenHawkIA on 2006-09-27
I had Qwest DSL and had [this problem]("http://www.ubuntuforums.org/showthread.php?t=173725") too (or a very similar one). The solution IS with disable IPv6, at least according to my experience & the person who responded to my thread, but the solution is to DISABLE it.  You can do it for the whole computer by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=87643"), under common application problems - Disable IPv6.

---

### Post by riverpaddler on 2006-09-27
You are talking to a real beginner here. I have read the information you suggested.  Am I to type in that line on the terminal and insert my username instead of the "uname" or am I to type it exactly as it is?

sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak/net/ipv6/ipv6.ko.bak

---

### Post by GreenHawkIA on 2006-09-27
Type it exactly as written.  A quick keyboard shortcut, Ctrl-C is copy, and Ctrl-V is paste, but when you are in the terminal you have to use SHIFT-Ctrl-C, and SHIFT-Ctrl-V, etc. etc.  Copying & pasting will make it a lot quicker.  It will ask you for your password in order to use sudo.

---

### Post by riverpaddler on 2006-09-27
WOO HOO!!!!!:p  I'm on!!! I typed it exactly as written and restarted and here I am.  Thank you so much, thank all of you for your help. Hoping to learn lots here and really start using Ubuntu!!

---

### Post by GreenHawkIA on 2006-09-28
> **riverpaddler said:**
> WOO HOO!!!!!:p  I'm on!!! I typed it exactly as written and restarted and here I am.  Thank you so much, thank all of you for your help. Hoping to learn lots here and really start using Ubuntu!!

Just so I know for future reference, when I give advice - was it the IPv6 disabling that did it for you?  And if so, who is your ISP?

---

