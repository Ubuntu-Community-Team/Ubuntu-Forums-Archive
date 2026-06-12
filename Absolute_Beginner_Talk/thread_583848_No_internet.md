---
title: "No internet"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rlj999 on 2007-10-20
Have installed 7.04  from Desktop CD -- have configured the network boxes for wired and wireless -- show no indication on upper bar of any network possibilities   -- this is a split install as I am running xp pro 
on the other partition 

Grub info:  choice is 2.6.20.15   generic mode .. 
Am unable to install network manager from Add/Remove program

Any help would be appreciated 

Robert

---

### Post by catfacts on 2007-10-21
Click the internet icon in the upper right of the screen, if you reconfigured your panels it is the network add-on, you should be able to select from a list of networks, If you need to eth0 is wire and eth1 is wireless.

---

### Post by rlj999 on 2007-10-21
> **catfacts said:**
> Click the internet icon in the upper right of the screen, if you reconfigured your panels it is the network add-on, you should be able to select from a list of networks, If you need to eth0 is wire and eth1 is wireless.

I have no internet icon in upper panel   -- having installed same 7.04 in a similar lap top I was looking for icon 

Robert

---

### Post by rlj999 on 2007-10-22
Still searching for help with internet access  -using 7.04  - icon on networking  appearing on upper  bar --unable to install network manager from Add/ons -- 

Would it be better if I reinstalled 7.04 --but would need to know how to insure the install goes to the right partition as I am running XZ and Linux  -- need to make sure I do not delete XP

Thanks

---

### Post by OffAxis on 2007-10-22
are you trying to get a wired connection going or a wireless connection?

what's the output of 
```
sudo ifconfig
```

---

### Post by rlj999 on 2007-10-22
> **OffAxis said:**
> are you trying to get a wired connection going or a wireless connection?

what's the output of 
```
sudo ifconfig
```

ifconfig output

eth1      Link encap:Ethernet  HWaddr 00:0F:B0:9A:85:9D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:13:CE:37:F6:11  
          inet addr:169.254.6.130  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:22 Base address:0x2000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:750 (750.0 b)  TX bytes:750 (750.0 b) 

robert@robert-laptop:~

Driver is a Intel I   Intel PRO wireless 2200 BG

Thanks

---

### Post by ruibernardo on 2007-10-23
Check if the eth0 section in /etc/network/interfaces looks like this:

```
auto eth0
iface eth0 inet dhcp
```

---

