---
title: "visual issues"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by uunbeliever on 2008-04-16
I just jumped off the Windows ship and installed ubuntu. My problem is however that the graphics seem low quality. When I try to bump up the visual effects it says it can not. I have ubuntu installed on a 750 mhz thinkpad and dont know if my video drivers are installed (or what they are). And I can not access the internet with my LAN port. Any help would be greatly appreciated.

I should have paid attention in computer studies!

Tackar, uunbeliever i Sverige

---

### Post by Jon Monreal on 2008-04-16
> **uunbeliever said:**
> I just jumped off the Windows ship and installed ubuntu. My problem is however that the graphics seem low quality. When I try to bump up the visual effects it says it can not. I have ubuntu installed on a 750 mhz thinkpad and dont know if my video drivers are installed (or what they are). And I can not access the internet with my LAN port. Any help would be greatly appreciated.

I should have paid attention in computer studies!

Tackar, uunbeliever i Sverige
Could you give us some more information on your computer?

You could see if there are any restricted drivers available for your graphics card and other hardware under System>Administration>Restricted Drivers.

Hope this helps you.

---

### Post by OffAxis on 2008-04-16
From a terminal type
```
ifconfig
```
to see how your networking is configured.

---

### Post by Tom--d on 2008-04-16
In Terminal, Type and paste the outcome of:

```
lspci
```
```
lsub
```

---

### Post by Tomatz on 2008-04-16
If its an old 750mhz P3 thinkpad i doubt you will be able to run compiz (visual effects).

Sorry :(

---

### Post by Jon Monreal on 2008-04-16
> **Tomatz said:**
> If its an old 750mhz P3 thinkpad i doubt you will be able to run compiz (visual effects).

Sorry :(
True.

But do you mean that the graphics seem unusually low quality (as in worse than they would have looked on Windows)?

---

### Post by Tomatz on 2008-04-16
They will as the gnome desktop is much more advanced than windows. Which will use more resources but in a better more efficient way than windows.

To get the most out of your thinkpad:

Open a terminal and type:

**sudo apt-get install xubuntu-desktop**

Wait for it to finish (might take a while)

Then **logout**

Select **session** at the login manager

Then **xubuntu**

**login**


You will now have a nice shiny xubuntu desktop that uses a lot less system resources ;)

Im using it right now on my eeepc.

---

### Post by uunbeliever on 2008-04-17
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21791 (21.2 KB)  TX bytes:21791 (21.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:B9:6F:FE  
          inet addr:130.236.216.210  Bcast:130.236.219.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:66ff:feb9:6ffe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128988 errors:0 dropped:630 overruns:0 frame:0
          TX packets:8348 errors:952 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19975319 (19.0 MB)  TX bytes:1515604 (1.4 MB)
          Interrupt:11 Memory:d893c000-d893c100

---

### Post by uunbeliever on 2008-04-17
jason@HAL9000:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
jason@HAL9000:~$ lsub
bash: lsub: command not found

---

### Post by northern lights on 2008-04-17
> **uunbeliever said:**
> jason@HAL9000:~$ lsub
bash: lsub: command not found

Typo. Tom meant to ask you to run "lsusb"...




> **uunbeliever said:**
> jason@HAL9000:~$01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

Forget about processing power, compiz would certainly run on a 700mhz machine, if it came with sufficient RAM and a powerful graphics chip.

A Rage chip will not do though, I concur with the previous posts.

---

### Post by sayakb on 2008-04-17
> **northern lights said:**
> A Rage chip will not do though, I concur with the previous posts.
 
+1. Compiz will not work with Rage. You have to stick with metacity WM. You might try out the gtk themes at [www.gnome-look.org](www.gnome-look.org) to beautify your desktop.

---

### Post by uunbeliever on 2008-04-17
In other words, deal with the non smoothness of fonts in openoffice or buy a newer laptop. Thanks for the graphics help. Now about the LAN problem. . .

Bus 001 Device 001: ID 0000:0000

---

### Post by northern lights on 2008-04-17
For the LAN issue, can you post the outputs of ```
lshw -C network
``` and ```
route -n
``` and maybe ```
cat /etc/network/interfaces
``` also? Thanks.

---

### Post by sayakb on 2008-04-17
> **uunbeliever said:**
> In other words, deal with the non smoothness of fonts in openoffice or buy a newer laptop. Thanks for the graphics help. Now about the LAN problem. . .
 
Bus 001 Device 001: ID 0000:0000
 
Non smoothness of fonts? Did you try sub-pixel smoothing. It works without compiz anyway, so it should work for you.

---

### Post by ByteJuggler on 2008-04-17
> **LinuxIsInnovation said:**
> Non smoothness of fonts? Did you try sub-pixel smoothing. It works without compiz anyway, so it should work for you.

+1 for sub pixel smoothing.  Also there's several additional font packages you can install which may help give you a wider variety of (possibly better looking) fonts in various contexts.

---

### Post by uunbeliever on 2008-04-17
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=66 maxlatency=56 mingnt=8
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0f:66:b9:6f:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.33 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b linked
jason@HAL9000:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
jason@HAL9000:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

---

### Post by northern lights on 2008-04-17
The routing table looks fine, the DHCP seems also be working and assigning you an IP. What exactly do you mean by the LAN port not working? Have you tried anything but opening websites in firefox?

If not, check with a different browser, try to ping some domain and report back...

---

### Post by uunbeliever on 2008-04-17
Network icon says " no network devices have been found" when I unplug my wireless adapter. The little green light is on on the port, but no internet

---

### Post by northern lights on 2008-04-17
mkey. So your "route -n" output is with the USB adapter connected? Can you do the same without?

---

### Post by uunbeliever on 2008-04-17
this is with the wireless card removed

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 
I am not sure I understand what you mean about USB adapter. My wireless card is PCMCIA, there is nothing in my one and only USP port.

---

### Post by northern lights on 2008-04-17
I dunno how the USB thing entered my mind. I somehow thought the wireless was via a USB dongle.

Cancel my last thoughts anyways - as you can see yourself, with the wireless removed, there ain't no IP assigned, the DHCP is not working and thus the pinging or a different browser irrelevant also. My bad.

With it removed, can you also post ```
cat /proc/network/interfaces
``` again, and maybe also the output of ```
ifconfig
```

I assume that will give the loopback only and no ethx either, but let's see...

---

### Post by uunbeliever on 2008-04-19
jason@HAL9000:~$ cat /proc/network/interfaces
cat: /proc/network/interfaces: No such file or directory
jason@HAL9000:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)

---

