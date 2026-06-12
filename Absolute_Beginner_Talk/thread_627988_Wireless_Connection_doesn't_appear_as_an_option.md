---
title: "Wireless Connection doesn't appear as an option"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-11-30
I only have options of wired connection or modem connection - there is nothing for wireless, and I don't know what I need to do to get this up and running.

Can anyone help please?!

Thanks!

---

### Post by parm289 on 2007-11-30
What wireless card do you have (Brand name and model)?

---

### Post by 449 on 2007-11-30
Go to 'Synaptic Package Manager' under Administration and make sure you have the two ndiswrapper packages installed.

---

### Post by bobyy on 2007-11-30
hy ..post here  please the output of :

> #lshw -C network
#lspci

---

### Post by parm289 on 2007-11-30
I'll give you the basic steps to take to install the drivers, because I don't know what card you have:

1.  Go to Synaptic Package Manager (System>Administration.Synaptic Package Manager) and run a search for "ndiswrapper" (without the quotes).

2.  Install all packages necessary for ndiswrapper (synaptic should automatically do this for you).

3.  Once ndiswrapper is installed, insert your wireless card's windows setup cd into your drive.  If your card didn't come with a cd, go to your brand's website and download the drivers there.

4.  On the cd, look for a folder that contains the drivers for your model (should be in a "Drivers" folder that has your model's name) and copy this to your hard drive.

5.  Go into ndiswrapper (System>Administration.Windows Wireless Drivers) and click the install drivers button. Browse to where you copied the driver folder and select the .inf file inside the folder.

After doing this, you should be able to go into wireless configuration and select a wireless network.

---

### Post by qprfact on 2007-12-02
OK - thanks for responses!

I installed the two ndiswrapper options in Synaptic.

My router is a Belkin. I'm running Ubuntu under Parallels Desktop on a MacBook Pro with Leopard.

Output of lshw -C network is:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth0
       version: 00
       serial: 00:1c:42:61:7a:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=10.211.55.4 latency=0 module=ne2k_pci multicast=yes
```

Output of lspci is:

```
00:02.0 VGA compatible controller: Unknown device 1ab8:1131
00:03.0 Bridge: Unknown device 1ab8:1112
00:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 02)
00:1e.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 08)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)

```

Windows Wireless Drivers doesn't appear as an option in Administration

---

### Post by bobyy on 2007-12-02
Bad news your wirelles is not recognized.......but let me understand ..actuali you run ubuntu in a virtuall machine ..yes ?in this case the network will work for ubuntu via LEOPARD 
it will be a bridged connection..so you dont need wirelles on ubuntu it is enought just the Mac wirelles...let me know if i am right or not
A good idea when you start a thread , if you expect right answers , is to put all the info about your problem .... :)
I se you install some programs... how you installit...? your network is working ...! you are in VMachine you expect to have a wirelles conection betwen host machine (your Mac) and virtual ubuntu ??..so anywai you have no wirelles interface on that machine(maybe phisicalli it is but not recognized by the ubuntu system)

  best wishes ! bobyy

---

### Post by qprfact on 2007-12-03
Yes, I am running in Virtual Machine in Leopard.

I have managed to install updates and other programmes in Ubuntu, but have had to do so by connecting a network cable to the machine and clicking on Wired Network Connection. This is fine if I am in one place, but obviously not so good for roaming!

So far as I can see, Ubuntu is not picking up the wireless aspect.

---

