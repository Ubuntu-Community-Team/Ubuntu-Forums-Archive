---
title: "Downloading Problem"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by jontes on 2008-01-06
hi

Im using a Telstra Broadband and most times i try to download a file over the size of 10 mb the download freezes at about halfway. Is there anyway for me to fix this? 

thanks in advance

---

### Post by Sef on 2008-01-06
What operating system are you using?

System specs?

---

### Post by jontes on 2008-01-06
im using 7.10.

---

### Post by bwtranch on 2008-01-06
Need a little more than that, bro. Post the out lsusb and lspci put of ifconfig for starts. Please. lsusb and lspci wouldn't be bad either.

---

### Post by jontes on 2008-01-06
lol i dont no much about computers so im not sure what your talking about.

---

### Post by bwtranch on 2008-01-06
That's Ok. Just go to Applications -> Accesories -> Terminal  and you should see something like this:

jim@jim-desktop:~$ 

Then just input the commands

jim@jim-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:6B:AD:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:17:3F:FD:2E:14  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fefd:2e14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:381927 errors:28676 dropped:2861 overruns:0 frame:28575
          TX packets:101295 errors:79 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:207163728 (197.5 MB)  TX bytes:6638302290 (6.1 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jim@jim-desktop:~$ lsusb
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 002: ID 04f9:0112 Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 050d:705c Belkin Components 
Bus 001 Device 001: ID 0000:0000  
jim@jim-desktop:~$ lspcci
bash: lspcci: command not found
jim@jim-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
jim@jim-desktop:~$

---

### Post by aktiwers on 2008-01-06
He wants you to go to terminal (applications => Accessories => Terminal)

And type in those commands. They will give an output that you need to copy/paste here for us to see.

```
lsusb
```
```
lspci
```
```
ifconfig
```



But what are you trying to download? Does this happend to all downloads or just those?

---

### Post by jontes on 2008-01-06
alot of stuff. programs game trials etc and what commands should i enter?? lsusb etc or the other ones

---

### Post by bwtranch on 2008-01-06
Okay, forget about the terminal for now. Just go to Add/Remove  and there should be all the things you need for now,

---

### Post by aktiwers on 2008-01-06
Maybe its your internet connection who is disconnecting?

You can always try use wget from the terminal.
```
wget -c http://www.SOMEWEBSITE.com/SOMEGAMETRAILER.avi
```

Change the link to whatever the link is to your file.

---

### Post by jontes on 2008-01-06
thnx alot for all your help.

---

