---
title: "Wireless Card from Marvel Tech not detected in UBUNTU"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by kunalbelnekar on 2007-01-16
Hi,
This is my first post on a Linux Forum ever. I think its really kool and am trying to play around with it.:o 

I am trying to install a Wireless card on my friends machine to get him to start using Linux too.For some reason it does not show up when I go to System -> Administration -> Networking.

I have done the following things

1. Installed the mrv8000c.INF that I got from the CD
2. Installed the mrv800c.SYS from the CD too (I uninstalled it since ndiswrapper -l was showing it as an invalid driver)
3.Installed another mrv8000c.inf from the wiki for wireless cards on Ubuntu.
Doesnt show up no matter what I do.

Here are the outputs for a few diagnostic commands that I ran

1. devang@devang-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:03:03:7E:5D  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe03:7e5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3252 errors:0 dropped:0 overruns:1 frame:0
          TX packets:1154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:891649 (870.7 KiB)  TX bytes:171747 (167.7 KiB)
          Interrupt:5 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.8 KiB)  TX bytes:1920 (1.8 KiB)

2. devang@devang-desktop:~$ lspci
01:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

3. devang@devang-desktop:~$ ndiswrapper -l
Installed ndis drivers:
mrv8000c        driver present, hardware present 

4.devang@devang-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



I havent tried popping the pci card out and reseating it again.I dunno if it works in Linux but it worked in Windows.

ANY SUGGESTIONS ???:confused:

---

### Post by rdd on 2007-01-16
Check out this thread, especially the last post.

[http://www.ubuntuforums.org/showthread.php?t=208088&highlight=88w8335](http://www.ubuntuforums.org/showthread.php?t=208088&highlight=88w8335)

cheers

rdd

---

### Post by kunalbelnekar on 2007-01-16
IT WORKED !!!!!!:D 

Thank you so much...last time I did it on my laptop I spent 4 days trying to figure out what was going on.It was a different card though.

But THANK YOU soo much !! :-({|= =D> :-\"

---

