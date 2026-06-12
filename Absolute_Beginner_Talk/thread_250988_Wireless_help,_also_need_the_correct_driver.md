---
title: "Wireless help, also need the correct driver"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Retnuh on 2006-09-04
I have been trying to use the WinXP driver that is on my Install CD for my Netgear WG511v2 PCI PC card. It says that the driver is invalid when I install it. 
When I load the driver in the little tutorial below that I somone pointed me too, I get the Driver present, but the Hardware wasnt present. It didnt show up, I do not know if my system is not seeing the card, or it had to do with the wrong driver. 
I will list info on the network here too, before I put the tutorial that I have been following.

Network information:

```
  *-network
       description: 88W8310 802.11g Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 0
       resources: irq:169
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:fa:67:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.1.105 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdff000-dfdfffff ioport:df40-df7f irq:201
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@03:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       resources: iomemory:22000000-2200ffff iomemory:22010000-2201ffff irq:169

```



Now this is the tutorial that I have been following. I am putting it all here so you do not have to flip back and forth pages. I have made it to step 4 but it comes out wrong.

```

1. Unload the prism54 module.

Before getting ndiswrapper, unload the prism54 module from your system. Ubuntu detects the WG511v3 on boot and loads the prism54 module. Although this card does have a Prism chipset (you can find out by typing "lspci" in the terminal), v3 is not currently supported by the prism54 project:
Code:

sudo modprobe -r prism54



Also, add a line containing the following to the /etc/hotplug/blacklist file using your favorite text editor (must have root privelages).

Code:

prism54


That will prevent your system from loading the prism54 module at boot. (Thanks bimberi)

2. Install ndiswrapper.

Code:

sudo apt-get update sudo apt-get install ndiswrapper-utils


3. Download the driver.

cd into a directory you prefer and type in terminal and:
Code:

wget http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip


Please let me know if the above step doesn't work. If you get a 404 error, it may just be that the file no longer exists at that location.
Unzip the file:
Code:

unzip AV\DR_2802wV.2_WHQL.zip



4. Load the driver.
cd into the "Driver" directory and cd into the "WinXP" directory. In this directory, you should see a file named "2802W.inf". In the terminal, type:
Code:

sudo ndiswrapper -i 2802W.inf


Check to see if the last step went okay with:
Code:

sudo ndiswrapper -l


You should see:
Code:

Installed ndis drivers: 2802w driver present, hardware present


*** gt24 told me (see below) that the drivers on the CD worked just fine and that the link I've posted above no longer works. If anyone finds a working link for v3, let me know and I'll update this. ***

5. Load the ndiswrapper module.

Code:

sudo modprobe ndiswrapper


Make sure everything went okay. Type in the terminal:
Code:

dmesg


Hopefully, you will see the following at the end of this output:
Code:

[4298557.630000] ndiswrapper version 1.1 loaded (preempt=no,smp=no) [4298557.760000] ndiswrapper: driver 2802w (SMC,04/29/2004, 3.0.11.1) loaded [4298557.771000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002) [4298557.771000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10 [4298557.772000] ndiswrapper: using irq 10 [4298561.706000] wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx using driver 2802w, configuration file 1260:3890.5.conf [4298561.706000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP

Your hardware should now be good to go. Please note that the x's above will be replaced by your NIC's MAC address.

6. Connect to the internet.

Use the Network Adminstration Tool in Breezy to connect to your router. This should be the easiest part. If you run into trouble with this last step, please check other posts and the Wiki before posting here.

7. Make things easy.
If you are successful and don't want to have to modprobe ndiswrapper after every boot, simply do the following:
Code:

sudo ndiswrapper -m


Also, please let me know of any errors in this post. I'm not sure if what I pasted as far as the dmesg output goes, will be what you get, especially the #'s in the brackets, but you should see the text not bracketed. (If this is wrong, someone please let me know.
```

Please help me out with finding the driver that works for my card. I have tried everything, but it is not working for me.

I have been trying this for days to get this wireless to work, but no luck.
I am a linux noob, and had no idea what all these commands were for until my friend told me about the Terminal and some useful commands.

Please help, Thanks....

---

### Post by Retnuh on 2006-09-04
Bump...
Need some help on this someone.
Thanks

---

### Post by almrking on 2006-09-04
I, too, had problems using ndiswrapper to try and get a D-Link usb wirelss card working. After fooling with it for a week I decided to go another route. If you get to that point, I have a suggestion. I bought a TrendNet TEW-443PI PCI card for about $28.00 at newegg.com and Ubuntu 6.06 recognized it without me having to do anything and I was literally connected to the internet and my home network in a matter of 2 minutes. It was truely plug and play. It is so good, it picks up other wireless networks in my neighborhood. All this for twentyeight dollars. Card info at:[http://www.newegg.com/Product/Product.asp?Item=N82E16833156165](http://www.newegg.com/Product/Product.asp?Item=N82E16833156165)

---

### Post by Retnuh on 2006-09-04
I hope I do not have to spend any money, but might have to. I would have to go back to WinXP. I was doing this to save money down the road and to learn.

I still would like some help.
I just found Marvel's website and downloaded the exe on my other computer, but am afraid to load it. This is supposed to be the correct new updated driver. But it is an exe file. :(

---

### Post by almrking on 2006-09-04
Take a look at this page. It has a wealth of information.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by Retnuh on 2006-09-04
I have done this and it does not work.
Still need more help.
I think I need a certain driver for my wg511v2.

---

### Post by Retnuh on 2006-09-05
Still need help.
Pretty Please..

---

### Post by Retnuh on 2006-09-05
bump*

---

