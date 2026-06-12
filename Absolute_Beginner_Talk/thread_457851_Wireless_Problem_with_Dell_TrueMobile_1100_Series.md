---
title: "Wireless Problem with Dell TrueMobile 1100 Series"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by dante244 on 2007-05-29
I just finished installing Ubuntu 7.04 on an old Dell Latitude CPx laptop and am having trouble getting my Dell Truemobile 1100 series wireless LAN adapter to connect to my wireless network.  

Before installing Ubuntu, I booted from the CD and was able to connect to the internet via my wireless network (I checked because I don't have a ethernet port on the computer).  After the installation completed and I restarted from the hard disk, the connection no longer worked under the same settings.  When I reboot from the CD, I can connect to the network again.  Any suggestions?

---

### Post by Kobalt on 2007-05-29
We would need more info wabout that card : can you post the output of the command line ```
lspci
```

---

### Post by dante244 on 2007-05-29
The output is as follows:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

---

### Post by mi_were on 2007-05-29
> **dante244 said:**
> The output is as follows:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

I wouls have to say that you would most likely have to install the wireless drivers using "ndiswrapper". There are wonderful tutorials and how-to in the community that I will not try to do one here. Suffice to say that it is straight forward (after struggling to do it!) 

The long and short is
1. install ndiswrapper-utils in synaptic
2. install the windows driver for the wireless device
 $ sudo ndiswrapper -i /pathtodriver/driver.inf
3. check the install
 $ sudo ndiswrapper -l
this should list the driver installed and indicate that the hardware is present.

get back if there is any problem (most probably will be!)

---

### Post by dante244 on 2007-06-03
Here's what I did:
1.  Did a clean install of Ubuntu 7.04 on my laptop (since I've been messing around with things).
2.  Inserted Ubuntu 7.04 install disk, hoping to install ndiswrapper using Synaptic Package Manager (because I don't have any other way to connect to the internet), but it doesn't seem to be on it.
3.  Inserted Ubuntu 6.06 install disk, and installed "ndiswrapper-utils" using Synaptic Package Manager.
4.  I assumed that the appropriate driver for my Dell Truemobile 1100 Series card is the NDIS5 driver based on this website:
[http://support.dell.com/support/edocs/network/079nk/specs.htm]("http://support.dell.com/support/edocs/network/079nk/specs.htm")
5.  I downloaded the NDIS5 driver for Microsoft Windows Server 2003, Windows XP, Windows 2000, Windows ME and Windows 98 version 4.5.1 from this web page:
[http://www.amd.com/us-en/ConnectivitySolutions/ProductInformation/0,,50_2330_6629_2452%5E2454%5E2486,00.html]("http://www.amd.com/us-en/ConnectivitySolutions/ProductInformation/0,,50_2330_6629_2452%5E2454%5E2486,00.html")
6.  I transferred this file from my other computer to my Dell laptop using a USB drive and placed it in my home folder.  I then ran the following line in Terminal:
sudo ndiswrapper -i /pathtothedriverijustinstalled/netamd.inf
The only output:
Installing netamd
7.  I then checked the install using the following command:
sudo ndiswrapper -l
The output:
Installed ndis drivers:
netamd          driver present 
8.  Out of habit, I restarted the computer.
9.  Upon startup, I looked at the available wireless connections in the drop down list, and selected my wireless network.  The wireless Network Key Required window came up, I selected the appropriate Wireless Security and entered the Passphrase, and then attempted to connect.  It didn't work.
10.  I then went to manual configuration.  I have three options: Wireless connection (wifi0), Wireless connection (eth0), and Modem connection (This network interface is not configured).  These are the same options I had before I installed the ndiswrapper.
11.  I tried a Manual configuration for both eth0 and wifi0 independently and together.  Whenever the eth0 was connected, it acted like it was connected to the network, but I couldn't connect to the internet using my browser.

The laptop that I'm installing Ubuntu 7.04 previously had Ubuntu 6.06 installed (at least I think it was - I haven't found the installation disk to confirm), and was able to connect to the internet if I manually configured the internet connect (using eth0).  I've since attempted to reinstall Ubuntu 6.06 and I can no longer connect to the internet with the same manual settings (which is why I'm wondering if I somehow had a version of Ubuntu other than 6.06).  

Any other suggestions?  Hopefully this helps...

---

