---
title: "Self inflicted but....Internet very slow on Ubuntu can anyone help?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by mark.tj on 2008-02-18
My system was working fine straight out of the box until I started messing with Virtual Box which although that is OK and the version of Windows inside Virtual Box connects to everything OK Ubuntu now does not.

Here are the copies of my interface and routing table

[HTML]marktj@linspeedy:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1D:60:23:5F:A7
          inet6 addr: fe80::21d:60ff:fe23:5fa7/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462 errors:0 dropped:0 overruns:0 carrier:37
          collisions:0 txqueuelen:1000
          RX bytes:462898 (452.0 KB)  TX bytes:93496 (91.3 KB)

marktj@linspeedy:~$ netstat -nr
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.1.2.4        0.0.0.0         255.255.255.255 UH        0 0          0 tap0
10.1.2.0        0.0.0.0         255.255.255.0   U         0 0          0 br0
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 tap0
0.0.0.0         10.1.2.8        0.0.0.0         UG        0 0          0 br0
marktj@linspeedy:~$[/HTML]

It looks to me like the irtt interface is wrong in the routing table, if so how can I change this?
Any help would be much appreciated

---

### Post by hyper_ch on 2008-02-18
tried disabling IPv6?

---

### Post by mark.tj on 2008-02-18
Thanks, I presume to disable I need to select Local Zeroconf network within the connection settings, I have done that and now get the following in the routing table 

[HTML]Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.1.2.4        0.0.0.0         255.255.255.255 UH        0 0          0 tap0
10.1.2.0        0.0.0.0         255.255.255.0   U         0 0          0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 tap0
0.0.0.0         10.1.2.8        0.0.0.0         UG        0 0          0 br0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0[/HTML]

It feels a little better but still slow, did I do this right?

---

### Post by mark.tj on 2008-02-18
Couple of other things. I am on a fixed ip with my own router 10.1.2.4 and the router itself is the gateway on 10.1.2.8
I fixed the ip because of something to do with virtual box which may have caused the problem in the first place but should still work.

---

### Post by bumanie on 2008-02-18
From what is in your post, I'm not sure diabling/blacklisting ipv6 will help, but it may be worth trying.

> sudo gedit /etc/modprobe.d/blacklist
At the bottom of the list, add 
blacklist ipv6
Save, reboot and see if it helps. If it doesn't help, get the list back, delete what you added, save and reboot. Your system will be back to how it was.

---

### Post by mark.tj on 2008-02-18
Thanks for that, didn't really make any difference but anything is worth a try

---

### Post by LeAstrale on 2008-02-18
is it only your browser thats slow or is Synaptic and others slow too ?

---

### Post by bumanie on 2008-02-18
Didn't think the ipv6 thing would work, but as you said, "Worth a try." Are you using gutsy or feisty?

---

### Post by mark.tj on 2008-02-18
I am using Gutsy(64) and in answer to the other question.. yes now I come to think of it a number of things within the system have started to take significantly more time to work its just connection to the Internet that is affecting me the most today. 

My system should be lightening being Quad core although it is Intel which I know is not the preferred option for Ubuntu.

---

### Post by bumanie on 2008-02-18
I still use feisty 32bit, so am not that good with gutsy 64, however has there beena kernel upgrade in the last couple of days. There was for feisty and that slowed my computer heaps. I uninstalled the latest kernel via synaptic and my pc basically began performing how it had previously. I assume the new kernel caused some type of hardware conflict. Just a thought, may not be applicable to you.

---

### Post by mark.tj on 2008-02-18
I think you could be right as I installed an update recently. I can use Synaptic OK but how do I actually find the latest Kernel release to remove? What section would it be under?

---

### Post by bumanie on 2008-02-18
Sorry, I've been offline for a while (I'm at work).Your boot screen will show you your kernel versions. Also (working on memory here as I'm on windoze machine) can go into the file system find boot folder and inside there you should find the grub folder that should have have the kernels installed listed. Basically, the one with the highest numerical value will be the latest. Note it down, go to synaptic, type kernel into search and then mark that kernel number for complete removal. I tried just do just do a removal, but it returned, that's why I ended up opting for the complete removal option.
Hope it works OK. Just make sure that you have the previous kernel to boot off.

---

### Post by mark.tj on 2008-02-18
Thanks for all your help I will try that tomorrow. Unfortunately  I think I will probably have to put Vista on this machine at some point because I bought it primarily for video editing and I have been unable to find a suitable Linux alternative, Virtual Box is fantastic but I loose half the power of the machine to run it which is a bit pointless really.
I am no expert so this has been an interesting journey that started with Linspire just before Christmas I have lost a number of man days getting this system to work but it is worth it and I have done it as a complete novice without the need for any help until today. I intend to install Ubuntu onto my older Athlon system with monitor sharing, having a system that is immune to virus and bugs etc has been very nice. 
When you get used to Linux it really is better.

Thanks again for your help today

Mark.

---

### Post by mark.tj on 2008-02-18
Thanks for all your help I will try that tomorrow. Unfortunately  I think I will probably have to put Vista on this machine at some point because I bought it primarily for video editing and I have been unable to find a suitable Linux alternative, Virtual Box is fantastic but I loose half the power of the machine to run it which is a bit pointless really.
I am no expert so this has been an interesting journey that started with Linspire just before Christmas I have lost a number of man days getting this system to work but it is worth it and I have done it as a complete novice without the need for any help until today. I intend to install Ubuntu onto my older Athlon system with monitor sharing, having a system that is immune to virus and bugs etc has been very nice. Might even try Xubuntu it might be quicker on an older system.
When you get used to Linux it really is better.

Thanks again for your help today

Mark.

---

