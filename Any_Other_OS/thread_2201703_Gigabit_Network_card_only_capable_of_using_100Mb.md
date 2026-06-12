---
title: "Gigabit Network card only capable of using 100Mb"
date: 2014-01-25
forum: Any Other OS
---

### Post by DeMus on 2014-01-25
Hi,
I have an Asus motherboard M5A97 R2.0 with an onboard Realtek networkchip RTL1111/R8168/8411:


```
inxi -Nn
Network:   Card-1: Realtek RTL8169 PCI Gigabit Ethernet Controller 
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8168 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: xx:xx:xx:xx:xx:xx
```


As you can see the speed of Card-2 is 100 mbps even though the card is a Gigabit card. The same happens when I connect the cable to Card-1.
This happens with every OS I have installed, or used in a live CD version.


My network contains only 1Gbps devices like the router and switches.


Now the strange thing: in virtual machines, using VirtualBox, I do get the 1Gbps connection, showing the card itself can handle it and so can my network. I have seen this in Windows 7, but also in several Linux distro's.


Linux Mint 16 KDE-64 in a virtual machine:
```
inxi -N
Network:   Card: Intel 82540EM Gigabit Ethernet Controller driver: e1000
```


As host I use also Mint16 KDE-64, so it is the same OS.
Can it be the driver, is it possible to use a driver for the Intel 82540 Ethernet controller like in the VM?
If so, how to install that one?


Who can help me?

---

### Post by Topsiho on 2014-01-25
Might this not be a bug in inxi? I use Ubuntu (12.04), which does not seem to provide inxi.

What does Connection information (Verbindingsinformatie) say when you click on the icon (up-arrow down-arrow) that gives you the information on wired and ethernet connections?

Topsiho

---

### Post by DeMus on 2014-01-25
The info I get here also says 100Mb. So I do think it is really just 100Mb.

---

### Post by jp734 on 2014-01-25
Is the router or switch you're using a gigabit router/switch as well? just wondering.

---

### Post by DeMus on 2014-01-26
Yes, the rest of the network is 1Gb as I wrote in my original post.
Even virtual machines have 1Gb connection, but the host sticks ate 100Mb.

---

### Post by Topsiho on 2014-01-26
I have two ethernet cards in my computer, of which one is the same as yours. Both use the driver r8169, where apparently you use r8168. I get 1000 Mb/s from both using this driver.

Topsiho

---

### Post by DeMus on 2014-01-26
After installing the OS I also used the r8169 driver, but with just 100Mb. After reading several threads on forums I installed the r8168 driver, hoping this would cure my setup, but no way.
I find it so strange that when I use a virtual machine, either Windows or Linux, I do have the 1Gb connection. How is that possible?

---

### Post by howefield on 2014-01-26
Thread moved to "*Other OS/Distro Support*" forum.

---

### Post by DeMus on 2014-01-26
I feel so stupid. All this time the answer to my problem was so easy. Yes, I do have a 1Gb card, a 1Gb switch, a 1Gb modem-router, but I don't seem to have a quality cable between the computer and the switch. (Still strange that the virtual machines do give me 1Gb with that cable)
I replaced the cable with another one and guess what: I now have 1Gb. Problem solved.

Thank you all for helping. I just sit in the corner now full of shame.

---

### Post by Topsiho on 2014-01-26
No need for shame.

Problem remains that in a virtual machine you got 1 GB, with the old cable. So problem is solved in a pragmatical way, but not really.
I feel ashamed I can't help you with this :)

Topsiho

---

