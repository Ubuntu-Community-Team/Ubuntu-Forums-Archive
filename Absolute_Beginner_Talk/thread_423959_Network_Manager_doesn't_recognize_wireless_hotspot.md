---
title: "Network Manager doesn't recognize wireless hotspots"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by diafygi on 2007-04-26
Hi everyone,

I'm slowly, but surely, making the jump from Windows XP to Ubuntu Feisty Fawn 7.04! But I've run into a snag and need the community's help. My Network Manager doesn't seem to want to recogonize any wireless hotspots (open or protected). I was involved in another thread earlier, but it turns out that our bugs were different, so I'm moving to a new thread. (old thread: [http://ubuntuforums.org/showthread.php?t=420124](http://ubuntuforums.org/showthread.php?t=420124) )

I'm completely new to Linux, so I'm feeling my way through this, but I've run a few commands (from advice of others) and gotten some info back. I have no idea if they are useful:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:90:F5:54:0A:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:52:B9:1D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 Memory:d0100000-d0100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:276 (276.0 b)  TX bytes:276 (276.0 b)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist eth1 scanning
```

eth1      No scan results

```

lsusb
```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
04:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
04:01.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

I've also attached a screenshot of my desktop with as many windows relevant to networking I can find.

A few questions:
-Why is my wireless called eth1? Shouldn't it be called wlan0 or something? Does that have any impact?
-when I boot to windows xp (i dual boot using grub), the wireless works fine. Would that mean my problem lies in Ubuntu, not a hardware issue?
-I am apparently using the restricted drivers that came with Feisty. Doest that mean I need a special program to use the hardware properly?
-What does "roaming mode" mean? Shouldn't Network Manager popup with "no wireless networks found" or "1 wireless network found"? Is there any way to force my card to rescan the area (like in windows xp)?
-I remember back when I was using the Feisty LiveCD, I could right or left click (I can't remember which) on the network manager taskbar (is that what it's called?) icon and a menu would popup with networks available. Then I installed Feisty and the popup menu went away. Now, I have to double click on the icon and the "Connection Properties" window appears. Could this be the problem? When the popup menu went away, I uninstalled the network manager package in Synaptic Package Manager, and tried wicd. I couldn't get it to work in the first 5 minutes, so I uninstalled it and reinstalled network-manager and network-manager-gnome.

I am soooo close to making the jump! Thanks so much ya'll (I'm from Texas)!

---

### Post by benfindlay on 2007-04-26
installing wifi-radar would allow you to scan for availalbe networks, but as for integrating it with network manager, I'm not sure if this would work. Personally I just set up the wifi network manually through network manager. If you are wanting to discover wifi networks that you do not know the name of I would definitely recommend installing wifi-radar!

Mine says roaming mode, which suggests it should allow scanning, but that depends on whether your hardware supports such scanning. In Xp, I think software gets round this problem, but I am not entirely sure.

Hope this helps!

---

### Post by DrTaylor on 2007-04-26
I'm having a similar problem. As far as I can tell, NetworkManager doesn't even know I have a wireless card. It doesn't even think I should have a wireless card. I have no option for wireless whatsoever. Do you know if there's a way I can remove NetworkManager and either reinstall it or replace it with something better? Is there anything better? Because this is not the first complaint I've heard about NetworkManager.

---

### Post by benfindlay on 2007-04-26
DrTaylor, does your computer recognise your hardware? You may first need to install ndiswrapper to get it to work. I had to do that with mine, and as soon as I had, it picked up the network without problems!

Hope this helps!

---

### Post by DrTaylor on 2007-04-26
Did that, and then it wanted me to install drivers and I was totally lost.

---

### Post by benfindlay on 2007-04-26
First of all put your wifi drivers (a *.inf file in windows) somewhere accessable.For example create a desktop folder for them called wifi

for ndiswrapper type the following into command line a line at a time:

```
sudo apt-get install ndiswrapper-utils-1.9
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf (perhaps /home/USERNAME/Desktop/wifi if you used my example)
sudo ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m
gksudo gedit /etc/modules

```

This opens a text editor - add > ndiswrapper to the end of the list and save! Then reboot and all should be well!

---

### Post by diafygi on 2007-05-15
It's been a while since I updated my status on this thread. It seems that my problem was a quirk in network manager. I did a complete reinstall of Feisty, and network manager is acting normal again. However, before I reinstalled Feisty. I found that Wifi-Radar was able to find hotspots before my reinstall.

Here's how I did it:
-Install wifi-radar from Add/Remove (all programs).
-Run wifi-radar
-Open network manager properties
-Disable roaming mode for my wireless card
-Select the network I want to connect to from the drop down list. Apparently wifi-radar populates this list when it is running. If I closed wifi-radar, the list would gradually disappear, one hotspot at a time. I would have to close the window and start wifi-radar again before I opened the window again.
-I don't think you need to keep wifi-radar running after you connect to a hotspot. However, you might need to run it again if you drop your connection with the hotspot. I don't think network manager is able to find the hotspot again without wifi-radar.

I'm doing this from memory, because now that I have reinstalled Feisty Fawn, my network manager seems to be able to discover hotspots on its own (although I have wifi-radar installed as a backup, just not running).

I now have a new problem regarding my wireless setup. Network manager does not give me the option of entering a WPA key, only WEP keys. I bet it has something to do with the restricted driver I'm using (Feisty installed it, I'm not using ndiswrapper). I can boot in Windows XP and connect to a WPA hotspot just fine. I haven't tried ndiswrapper yet, so we'll see. I'll post that problem in another thread if I can't solve it on my own. I'll document the whole thing on my wiki: [http://wiki.ubuntu.com/Diafygi](http://wiki.ubuntu.com/Diafygi) (though don't expect a fast resolution, cause this is a low priority).

I'm beginning to think that I might tell friends about Ubuntu, but they are going to ask about several things:
1. Can I force refresh/scan for wireless hotspots?
2. Can I create a ranked list of preffered hotspots, with their settings/keys saved?
3. Where does my computer keep saved keys?
4. When I reboot, I automatically connect to the wireless network I was on previously, but I have to type in my admin password so that network manager can retrieve the saved key. I know it's about security, but is there any way around this annoyance? I may not be the admin on my computer.
5. Is there a way to do all of these things without using the terminal?

All of these questions arise from Windows XP wireless configuration, where users can rescan and list/rank approved/saved hotspots. My friends aren't very technical, so the notion of a terminal is a huge turn-off.

Avast!

---

### Post by diafygi on 2007-05-19
So, me being an idiot caused this bug. Remember when I said that when I reinstalled Feisty it fixed the problem. Well, back before that, I had rearranged the panels to my own style (as you can see in my first screenshot). Apparently, I accidentally deleted the "Notifications Area" icon on the panel. Since the only *notification* in the area at the time was the *Network Manger * icon, I thought that I had deleted the network icon. So when I added the icon back to the panel, I added the WRONG ICON! Apparently the "Network Monitor" is not the same as the "Network Manager" (makes sense). However, it took me FOREVER to realize that the *Network Manager* icon resides in the *Notification Area* item. All I had to do to fix my bug was ADD THE "NOTIFICATION AREA" BACK TO THE PANEL. Wifi-radar was **not** needed.

me = noob

Here are some figures:
Figure 1 - The "Add to Panel" menu, with "Network Monitor" (bad) and "Notification Area" (good) circled
Figure 2 - What the "Network Manager" and "Network Monitor" icons look like when disconnected
Figure 3 - What the "Network Manager" and "Network Monitor" icons look like when connected

I think a part of this should be blamed on poor user interface design. How in the hell was I supposed to know that the little network manager icon was in the notification area. I saw a network icon, I added it, and it caused a new thread to be filed in the beginner section of a great community. :(

---

