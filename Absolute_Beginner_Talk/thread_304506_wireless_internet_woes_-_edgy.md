---
title: "wireless internet woes - edgy"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by ridgeback on 2006-11-21
I am new to linux, I installed it on my desktop a few days ago, and on my laptop today.  I am trying to configure my wireless internet, and I just don't really know how. I have read some other threads but they lose me quickly, and I have some reading material for anyone who is willing to help me get started:

```
jerod@jerod-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:22:67:0C  
          inet addr:131.212.147.216  Bcast:131.212.147.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe22:670c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:431536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:132690 txqueuelen:1000 
          RX bytes:374669544 (357.3 MiB)  TX bytes:13627603 (12.9 MiB)
          Interrupt:193 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:DB:A1:53  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


and

```

jerod@jerod-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

iface eth1 inet dhcp
wireless-essid NETGEAR
wireless-key ClintEastwood
```

Note that the essid and key are figures I put in myself when trying to connect.  I am trying to connect to a hidden wireless network with that id and password.
and


```
jerod@jerod-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:22:67:0c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half ip=131.212.147.216 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:e00fc000-e00fdfff irq:193
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:db:a1:53
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e00f6000-e00f7fff irq:177
```


My laptop is a Gateway model 7330GZ and my wireless card is a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03).

Any ideas from anyone would be greatly appreciated.  Thanks.

-Jerod

---

### Post by groggyboy on 2006-11-21
It looks like your wireless card is recognized, which is good.  It also looks like you have your wired connection working and its connected to the internet.  I'm gonna assume you do.

Personally, I like using network-manager to take care of my wireless.  I'm a big fan of easy-to-use gui's, and this app's got it.  Plus it supports wpa, lets you pick wifi networks from a drop-down menu, and automatically switches to wired if its available.

To install it, type this in a terminal.  if you use kubuntu, replace "network-manager-gnome" with "knetworkmanager".```
sudo aptitude install network-manager network-manager-gnome
```

Hit Ctrl-Alt-Backspace to leave your GNOME session and get back to the logon screen.  After you log back in, the network-manager applet should appear in the systray beside the clock and the volume icon.

one last thing before you can start using it.  from the terminal, edit the /etc/network/interfaces file ("sudo gedit /etc/network/interfaces") to
make it look identical to this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

You should be able to do everything from the icon in the systray now.  If the essid name of your network is not broadcast, left click on the icon and choose "Connect To Other Wireless Network..." from the menu - you can fill it in from there.

if you like gui's, and don't need wpa support, you could also look into wifi-radar.
i've also been following the development of a new app called Connection Manager which has some improvements over network-manager.  its still in the works tho.  search the forums for it if you are interested.

have fun, and don't be afraid to ask for help if anything doesn't work!

---

### Post by ridgeback on 2006-11-22
network-manager didn't appear anywhere, despite a seemingly effective installation.  How can I get to it?  (not in system tray, not in applications)

---

### Post by ridgeback on 2006-11-22
Actually now I got it to appear, but I still can't connect, even with all of the correct information as read by another computer on the same network.  I think it has something to do with the wireless card on my laptop being enabled.  There is a light that indicated when my wireless was enabled when I was using windows, but now that I am using linux the keystroke to enable it doesn't work.  Is there some other way to check this?  The network I want to connect to isn't being broadcast, but the networking apps aren't picking up any of the other networks around, and I know for a fact they are there.  Anyone know what's going on?

---

### Post by groggyboy on 2006-11-22
perhaps you need to use ndiswrapper.  it lets Ubuntu use your wireless card's windows driver.  first, make sure you have the universe and multiverse repositories enabled - check [this article]("https://help.ubuntu.com/community/Repositories/Ubuntu") over at Ubuntu Documentation if you are unsure how to do that.

Then, in a terminal, type:```
sudo aptitude install ndiswrapper ndisgtk
```
After installation, run the app.  It's under System > Administration > Windows Wireless Drivers, and just run through the wizard.  Hope that works!

I didn't have to use ndiswrapper because my intel2200bg wireless card is supported out of the box.  however, ndiswrapper is fairly well documented - [this article]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") from the Ubuntu Documentation website is where I got my info.  Ndisgtk is the graphical front to ndiswrapper.  If you feel up to the challenge, there are instructions on that page on how to do it by using the terminal and configuration files.

Have fun!

---

### Post by metBANS on 2006-11-22
Well, I'm running Unbuntu on my laptop, and I need to be able to connect to my WPA encrypted network.  I did what groggyboy said to do in the terminal, but I'm assuming I need to be connected in order for that to work.  So is there anyway I can do this without the laptop being connected?

---

### Post by groggyboy on 2006-11-22
its easiest if you have access to a wired ethernet connection.  but if that's not possible, find another computer with internet access - i presume you can, because you were able to post here :p !

Go to the following sites and download the packages from packages.ubuntu.com (depending on your wireless card, ndiswrapper may not be nescessary):
[ndiswrapper-common]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.18-1ubuntu2_all.deb&md5sum=3d9fe86fb30086a4eba9aec6a4f06ef7&arch=all&type=main")
[ndiswrapper-utils]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb&md5sum=6ba955830847e6e20282291ff124b34d&arch=i386&type=main")
[ndisgtk]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main")
[network-manager]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.3-2ubuntu6_i386.deb&md5sum=522cade5b931785517c0fb2bb7035a1e&arch=i386&type=main")
[network-manager-gnome]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.3-2ubuntu6_i386.deb&md5sum=1f857fb5abaa57675e4695baf66289b5&arch=i386&type=main")
Save the files to a USB Stick, floppy disk, cd, etc, so you can copy them to your linux installation.

Once you are back in ubuntu, install them by using gdebi (just double click, it should be automatic - if you use GNOME).
**IMPORTANT:** make sure you install the files in the order I list them above.
then just follow my advice from there.

---

### Post by metBANS on 2006-11-22
I tried manually installing the packages, and it didn't work once I went into the terminal and entered the code you provided.  I tried it again, to make sure I didn't load the packages in the wrong order, and yet again it didn't work.  Also, when I connected a straight line from my router to the laptop, it didn't work, or even give me the option of configuring my wired connection. (I didn't do this before, because my router is in a storage room in my basement, and it is cold!)

If you need any other details, I can provide them.

I'm trying to configure a Dell Latitude C600 Laptop
I am using a D-Link AirPlus DWL-G650 wireless card

Thank you.

---

### Post by groggyboy on 2006-11-22
i'm not sure whether your issue is that the install didn't work, or that it worked but your card still isn't working...  :-?  what happens when you type "network-manager" in a terminal? 

if you get an error that says it can't be found or isn't installed, move the network-manager and network-manager-gnome .deb packages from the removable media to your /home folder and type these commands in the terminal to install them:```
sudo dpkg -i network-manager
sudo dpkg -i network-manager-gnome
``` 

your card (d-link airplus dwl-G650) uses an athero driver.  under linux, atheros uses madwifi (atheros, intel and ralink are pretty much the only wireless card makers that have native linux drivers - otherwise its ndiswrapper and crossed fingers).  unfortunately, i've heard that madwifi support under edgy(6.10) is a little rough.

which basically leaves you with two options: switch to dapper (6.06), or try to fix it in edgy.  according to [this thread]("http://www.ubuntuforums.org/showthread.php?t=293230"), your problem *may* have something to do with linux-restricted-modules not being installed.

provided you haven't tweaked your apt sources.list, this should work.  get your install cd ready, and type this in the terminal:```
sudo aptitude install linux-restricted-modules-$(uname -r)
```
then reboot, and try running network manager again.  get back to me if anything goes wrong.

---

### Post by metBANS on 2006-11-23
I'm thinking that the problem is the fact that I'm using a WPA encrypted connection.  How would I go about configuring to that?

---

### Post by PrinceArithon on 2006-11-23
It seems that you have lo instead of eth1 going.  As soon as you get your network manager running.  There should be some little computer screen icon in your system tray.  Right click on it click properties.  You should see lo or eth1 in the top box.  If you see lo instead of eth1, change it to eth1.  If it is already eth1 I'm sorry I'm not sure what else to tell you.

Well there is something else you could try with your wireless router.  If you hide your brodcast ID, turn off the encryption, and make it where the only way people can get onto the network is through the mac address, it can work too.

---

### Post by groggyboy on 2006-11-23
two pages from Ubuntu Documentation to help you:
[WirelessTroubleShooting]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
[WifiTroubleshooting]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting")

metBANS: As I mentioned earlier, I'm not sure where your problem is, so I figure its best to start troubleshooting from the top.

Taken from the troubleshooting pages: type "lshw" in a terminal to see if your computer is recognizing your card, and if there is a driver for it.  Look for any mention of D-Link, Atheros, or Madwifi.  If you see your card in the list, great.  Then we can move on to the next step!  If you can't make heads or tails of the output, paste it here and I'll take a look.

---

### Post by gils0040 on 2006-11-30
hey buddy, i was lookin at the ubuntu wiki for info on your wireless card and found this [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupportedhttps://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupportedhttps://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported). It doesnt say much for your actual card (the rev 3), but if you look at the wpc54g it uses the same chipset. So following the directions at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) is worth a shot. good luck!

youll probly have to search the repos for bcm43xx ( apt-cache search bcm43xx or just use synaptic (or adept i forget which one is included))

Edit: here i found this, seems to be the best guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Papa-san on 2006-11-30
I have a Dell Lattitude C-600, but it has the stock broadcom card in it:```
 *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:2c:52:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=192.168.2.45 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f8ffc000-f8ffdfff irq:5
```


This is my /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

#iface eth1 inet dhcp
#wireless-essid 06B408770040
#wireless-key s:xxxxxxxxxxx

#auto eth1

iface wlan0 inet dhcp
wireless-essid 06B408770040

#iface dsl-provider inet ppp
#provider dsl-provider

iface eth0 inet dhcp

auto wlan0

```
I am running Dapper because Edgy wouldn't work with my setup. (DSL modem/router)

If you use ndiswrapper, you need to blacklist the pre-installed bcm43xx driver that doesn't seem to work with the 4306... ```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```then```
sudo rmmod bcm43xx
```

You will need to get the drivers (bcmwl5.inf and bcmwl5.sys) saved onto your Desktop (file roller or archive manager will work. find the drivers on your install cd and convert the .exe to a .zip. then extract it to your desktop)

then: (one line at a time, 'entering' after each)```
 sudo modprobe -r ndiswrapper
sudo apt-get --purge remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rmmod ndiswrapper
```This assures you a clean palette!
Then:(one at a time, again)```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```re-boot, and it should come up for you. If it doesn't, run 'sudo modprobe ndiswrapper' again.

Then, in System > Administration > Networking you should find 'wlan0' listed as the wireless interface (You should actually see it forced during the 'sudo ndiswrapper -m' step)

DO NOT rename or mess with your 'lo' settings!!!!! This is your computers loopback interface. It willl be an UGLY thing if you change it! (Consider it a DNFW setting!)

I know this works with Dapper, and should have worked with edgy, but didn't in my case due to the router... 

Best luck!

---

