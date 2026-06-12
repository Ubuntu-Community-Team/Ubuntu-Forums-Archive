---
title: "Cant connect Windows98 to my Linux Ubuntu with Samba"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-06-05
I have installed and configured samba on my ubuntu server
and it looks ok.

But when I try to map network drive from Windows to my
ubuntu server wich has ipaddress (10.0.0.13). \\10.0.0.13\backup
i get a error message :

---------------------------------------------------------------
The following error occured while trying to connect
F: to \\10.0.0.13\backup

Windows cannot find the computer or share name. Make shure
that the share name is valid and that you are connected to the
network, and then try again.
----------------------------------------------------------------

Both the ubuntu box and Windows ME box are connected to the
network and internet. They are on the same workgroup, but they
cant communicate. I cant ping hostname, but pinging ipaddress
works fine.

How get samba to work so I can map network folders on my
Ubuntu from Windows ?

---

### Post by %hMa@?b&lt;C on 2006-06-05
type 
```
ifconfig
```
what is the output?

---

### Post by linuchsan on 2006-06-05
is samba started?

---

### Post by chrisdee on 2006-06-06
The output of ifconfig is :

christian@T3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:10.0.0.13  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:abff:fedd:28bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:590960 errors:0 dropped:0 overruns:0 frame:109
          TX packets:590123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37855102 (36.1 MiB)  TX bytes:62534575 (59.6 MiB)
          Interrupt:3 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8419166 (8.0 MiB)  TX bytes:8419166 (8.0 MiB)

christian@T3:~$

(Note that iv changed the mac address so its not publicly posted
out on this forum).

Samba is installed, but Im not shure how to check if it'r running.
How do I do that ?

---

### Post by linuchsan on 2006-06-06
ps -aux |grep smbd
ps -aux |grep nmbd

---

### Post by chrisdee on 2006-06-06
I solved the problem. I had to open samba port 137 and 139
in firestarter firewall.

---

### Post by chrisdee on 2006-06-06
Damn. I restarted windows and ubuntu and it doesnt work again.
Guess i need some more help. what can be wrong ?

When I try to run ps -aux |grep smbd i get :

root@T3:~# ps -aux |grep smbd
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      9302  0.0  0.5   9188  2716 ?        Ss   10:51   0:00 /usr/sbin/smbd -D
root      9303  0.0  0.5   9188  2704 ?        S    10:51   0:00 /usr/sbin/smbd -D
root      9505  0.0  0.1   3040   552 pts/1    R+   11:05   0:00 grep smbd
root@T3:~#



When I try to run ps -aux |grep nmbd i get :

root@T3:~# ps -aux |grep nmbd
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
1000      8561  0.0  0.3   6912  1776 ?        S    10:24   0:00 /usr/sbin/nmbd -D
root      9519  0.0  0.1   3036   544 pts/1    R+   11:06   0:00 grep nmbd
root@T3:~#

---

### Post by chrisdee on 2006-06-06
Also when i try to run smbclient it looks ok :

root@T3:~# smbclient -L t3 -U administrator
Password:
Domain=[TEXAS] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        print$          Disk      Printer Drivers
        backup          Disk      Backup folder
        IPC$            IPC       IPC Service (T3)
        ADMIN$          IPC       IPC Service (T3)
Domain=[TEXAS] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------
        T3                   T3

        Workgroup            Master
        ---------            -------
        TEXAS
root@T3:~#

---

### Post by chrisdee on 2006-06-06
Does anybody have any suggestions ?

---

