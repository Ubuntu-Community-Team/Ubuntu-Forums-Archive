---
title: "wireless connecting, Gateway laptop"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Corvair on 2008-02-28
Hello everyone,

I have a Gateway laptop model MX6453 with netgear wireless.

I have never been able to operate wireless and I would like to solve the problem.
here is what I get on Terminal. If anyone understands the following and can help me configure my wireless you are more than welcome.



claude@claude-laptop:~$ sudo iwconfig
[sudo] password for claude:
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"netgear"  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

claude@claude-laptop:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:A5:D0:2D:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:E0:B8:B9:AF:47  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:feb9:af47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24087706 (22.9 MB)  TX bytes:1214329 (1.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31586 (30.8 KB)  TX bytes:31586 (30.8 KB)

claude@claude-laptop:~$

---

### Post by oedha on 2008-02-28
sounds like broadcomm 43xx.......
try these.....
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
need more...maybe here :==> [http://ubuntuforums.org/search.php?searchid=37085733](http://ubuntuforums.org/search.php?searchid=37085733)

---

### Post by oedha on 2008-02-28
addition :
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=broadcom&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=broadcom&titlesearch=Titles)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29?highlight=%28broadcom%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29?highlight=%28broadcom%29")

for 4311 ==> [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29)

---

### Post by Corvair on 2008-02-28
Hello OEDHA
This is the number BCM94311MCG and not BCM43xx series.
So what can I do with this?.
I am not a wiss at this as you can see



claude@claude-laptop:~$ lspci | grep Broadcom\ Corporation
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
claude@claude-laptop:~$

---

### Post by oedha on 2008-02-28
i see.....:)
what about this :==> [http://ubuntuforums.org/showthread.php?t=697731](http://ubuntuforums.org/showthread.php?t=697731)

edit : it is 4311......i've given you about 4311

---

