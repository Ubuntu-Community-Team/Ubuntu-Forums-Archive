---
title: "New updates lost my wirless card, 7.10"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Jalazmi on 2007-10-07
Hi, i installed the recommended updates to ubuntu 7.10 beta last night then i lost the wireless connection and i cant configure it with terminal  


> jalazmi@Jalazmi:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:70:05:C4  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe70:5c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2859548 (2.7 MB)  TX bytes:672870 (657.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.1 KB)  TX bytes:1200 (1.1 KB)

jalazmi@Jalazmi:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
jalazmi@Jalazmi:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.



So i need some help if anyone can

---

### Post by irish_flu on 2007-10-07
As 'beta' software is not suitable for the beginner (it's buggy by nature; that's why it's a "test" release), this forum probably won't provide you with much help for it.

You'll get better responses to this question if you post in the Development forum.
[http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)

---

### Post by Jalazmi on 2007-10-07
Okey thx 4 ur help

---

### Post by nooby on 2007-10-07
I'm new to linux,
 the version of Ubuntu released october/november some 22 days from now. wouldn't that one be as stable as the version of 7.04 FiestyFawn we have now? Or do you mean I should download 7.04 now and only download 7.1 next year around February or so?  to let it work out all the bugs? I don't mind to wait 22 days without linux to try out but not many months for a stable Gutsy version.

---

### Post by dimbulb1024 on 2007-10-07
Gusty comes out in only 12 days. Once it comes out it will be fine to install. You will not have to wait for the bugs to be worked out. You don't have to wait for the bugs to be worked out ala Windows. ;)
So, you can install Feisty (7.04) now and upgrade in 12 days or just wait and install Gusty when it comes out.
Your choice

---

### Post by nooby on 2007-10-07
Maybe I do. I've tested Ubuntu 6. 06 Edgy Live CD but my DVD Rom player spins it too fast the sound from it is very disturbing. Wrooom. The Knoppix Live CD from 2003? was very quite comparably. So I downloaded WUBI instead. Great for getting a real feel for how Ubuntu Gnome looks and feels using it. 

But the shutdown problem seems not easy to do something about for us noobies, So people told me that if I do a real install thee problem will disappear. So I hope that is true.

---

