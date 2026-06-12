---
title: "kubuntu network prb"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by rasputin1575 on 2006-12-23
Hello peeps.
just struggling a bit with my internet connection.
my internet runs for a few mins and then stops by itself. i have to restart kubuntu all the time, and then, mins later, it does it again.
am new to linux so i might have configured the network wrongly. can anyone help me out pls
i've been fiddling with files like:-

/etc/network/interfaces
/etc/hosts
/etc/resolv.conf

am sure i must have done something wrong... 

also, could anyone tell me what would be the **network address** and the **broadcast address** if the ip address is 192.168.1.10 


Hope to hear from you guys soon,


Ash

---

### Post by Rippey on 2006-12-23
[QUOTE=also, could anyone tell me what would be the **network address** and the **broadcast address** if the ip address is 192.168.1.10[/QUOTE]

if your using the defauld subnetmask for that ip (255.255.255.0) the broadcast address would be 192.16.1.255 and the network address would be 192.16.1.0 , but that all depands on the subnetmask you're using.

now for your problem, could you post the contents of the files you mentioned and the output of ifconfig, maybe there is someting in the that would explain what is happening.

---

### Post by rasputin1575 on 2006-12-23
Hi,
thx for your reply. yes i am using defaulf subnetmask for that ip, hence (255.255.255.0).
this is my "interfaces" file:-

-----------------------------------------------
[B]auto lo
iface lo inet loopback

script grep
map eth0


auto eth0
iface eth0 inet static

address 192.168.1.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1


auto eth0:0
iface eth0:0 inet static

address 192.168.1.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1
[/B]
------------------------------

and this is what i get when i do "ifconfig":-

[B]eth0      Link encap:Ethernet  HWaddr 00:02:A5:A7:4E:43  
          inet addr:192.168.1.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fea7:4e43/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1525055 (1.4 MiB)  TX bytes:72684 (70.9 KiB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1136 (1.1 KiB)  TX bytes:1136 (1.1 KiB)[/B]
---------------------------------------------------------


as you can see, the broadcast and network address am using is different to the one you advised me to use. should i change it to yours?>
thx ,
ash

---

### Post by rasputin1575 on 2006-12-23
Rippey,
whenu wrote <quote>broadcast address 192.16.1.255 and the network address would be 192.16.1.0</quote>, did u mean instead 192.168.1.255, and 192.168.1.0 ?
rgds.
ash

---

### Post by Rippey on 2006-12-23
> **rasputin1575 said:**
> Rippey,
whenu wrote <quote>broadcast address 192.16.1.255 and the network address would be 192.16.1.0</quote>, did u mean instead 192.168.1.255, and 192.168.1.0 ?
rgds.
ash

oops, you're right, I got the wrong private ip ranges :eek: 

you should change bcast- and networkaddresses to the ones you've posted becouse in your current setup these addresses are on an other network.

if you're interested in the basics of networking [_here_]("http://www.pantz.org/networking/tcpip/subnetchart.shtml") is a good site to have a look at.

hope things will work now. :D

---

### Post by rasputin1575 on 2006-12-23
Hi,
thx, i'll try that.
another clarrification (sorry, am being a pain:) )
you wrote:-

"you should change bcast- and networkaddresses to the ones you've (**me??? - rasputin1575 ?**) posted becouse in your current setup these addresses are on an other network"

what you meant was in fact : the one's that **YOU (rippey)** posted ??
thx,
ash

---

### Post by Rippey on 2006-12-24
to avoid confusion:
bcast: 192.168.1.255
network: 192.168.1.0
:)

---

### Post by rasputin1575 on 2006-12-24
Thx Rippey,
done what u suggested. internet been working fine. in fact, for the first time i did a solid 3-4 hrs job on it b4 it stopped again (an improvement from the  10-15 mins i used to get).
Ash

---

