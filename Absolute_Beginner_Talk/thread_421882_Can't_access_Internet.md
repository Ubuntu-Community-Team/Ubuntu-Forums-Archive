---
title: "Can't access Internet"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Uncle Phil on 2007-04-24
[FONT="Comic Sans MS"][/FONT]
I am a new user.  I booted from a Ubuntu DVD (Ver. 6.06 LTS) and did not install on my hard drive.  I followed a link to a page for Ubuntu Networking for Basic and Advanced Users.  I followed directions to System/Administration/Networking and the window only shows a modem connection.  It does not show my wired connection.  My ethernet port is on the motherboard and not a separate pci card.  The computer is a Dell XPS 410 with serial drives if that makes a difference.  Do I need a separate ethernet card to be able to go on line?  Thanks in advance for any help you can provide.

---

### Post by Kobalt on 2007-04-24
First, let's check if your card is regonized and active. Can you please post the output of this command line : ```
ifconfig
```

---

### Post by Uncle Phil on 2007-04-24
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Zarkoff>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : hsd1.ct.comcast.net.
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\Zarkoff>

---

### Post by Uncle Phil on 2007-04-24
Sorry it took so long to respond.  I ran the ipconfig on windows to get the results.  Again my thanks.

---

### Post by oilchangeguy on 2007-04-24
you need to obtain this info while using the live cd. open a terminal and type the command there so it can be determined what linux is seeing.

---

### Post by Uncle Phil on 2007-04-24
I'm brand new, how do I open a command line?

---

### Post by Uncle Phil on 2007-04-24
Link encap:Local Loopback
inet addr:127.0.0.1  Mask: 255.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX Packets:7 errors:0 dropped:0 overruns:0 frame:0
TX Packets:7 errors:0 dropped:0 overruns:0 carrier:0
collision:0 txqueuelen:0
RX bytes:372 (372.0 b)  TX bytes:372  (372.0 b)

---

