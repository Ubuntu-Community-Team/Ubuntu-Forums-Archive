---
title: "help me with a wireless card"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by tasukete on 2007-03-09
I am Japanese ,in Japan.
I am not good English,sorry.

I am using wireless LAN card,"Buffalo WLI-CB-G54L".
It is not working.
(I can not do wireless LAN internet.)
("LINK" is lightning. "POWER" is not lightning.)

Please help me.

This is report.

username@username-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:3542-4344-3641-3138-3237-3144-45   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

username@username-laptop:~$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by xyz on 2007-03-09
Hi,
Not sure this will help but give it a try:
[HardwareSupportComponentsWirelessNetworkCardsBuffalo]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo")
[Read what "T-Rexx" says]("http://www.justusboys.com/forum/showthread.php?p=1925726")
...click on the links.

---

### Post by PartisanEntity on 2007-03-09
Do you need to connect to a wep or wpa encrypted wireless network?

---

### Post by tasukete on 2007-03-09
> xyz
I tried.
but i can not find the "FwRad16.bin".
Driver CD is install CD,isn't it?

> PartisanEntity
WEP.

---

### Post by PartisanEntity on 2007-03-09
Did you got to System > Administration > Networking  and configure Wireless connection ?

Edit: I personally would recommend the use of Network Manager, but lets see if you have configured it the normal way.

---

### Post by Bachstelze on 2007-03-09
Your card has a Broadcom chipset, which will require a bit of additional work do get up and running :

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by PartisanEntity on 2007-03-09
Im not sure he needs ndiswrapper as his card appears to be up and running but just not configured?

---

### Post by tasukete on 2007-03-09
> PartisanEntity
Yes.

At  "setting for interfase eth1", I check the top of  checkbox , typed "ESSID" and "Password" , selected "DHCP" , and clicked "OK" .
(My home's wireless network is using DHCP.)
And I checked eth1 ON checkbox.

---

### Post by PartisanEntity on 2007-03-09
How did you install the wifi card?

---

### Post by tasukete on 2007-03-09
>PartisanEntity
Sorry.I don't kwow the "wifi card".

I carried out this activity.

(1)
i had downroad.
[http://apt.ubuntu.org.tw/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb](http://apt.ubuntu.org.tw/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb)
[http://apt.ubuntu.org.tw/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb](http://apt.ubuntu.org.tw/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb)

(2)
I installed.
$ sudo dpkg -i ndiswrapper-xxx.deb

(3)
I had read and tried it.
[http://ubuntuguide.org/wiki/Ubuntu:Edgy_ja#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Edgy_ja#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

---

### Post by PartisanEntity on 2007-03-09
Please post the output of this command in the terminal: ndiswrapper -l

---

### Post by tasukete on 2007-03-09
$ ndiswrapper -l
Installed driveers:
bcmwl5               driver installed, hardware present
netcbg54                        driver installed, hardware present

---

### Post by PartisanEntity on 2007-03-09
Okay try this:

```
sudo apt-get install network-manager-gnome network-manager
```

And reboot your system, if you get an error message about cache after rebooting type this in the terminal:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

And reboot again.

Then you should see network-manager in the panel notification area.

---

### Post by tasukete on 2007-03-09
I tried
$sudo apt-get install network-manager-gnome network-manager
but, I see some of error message.
(My UBuntu is Japanese edition. Error messages is including Japanese. So I can not post error messages)

My UBuntu PC isn't / cannot connecting Internet.
(Because I have no LAN cable.)

---

### Post by PartisanEntity on 2007-03-09
Are you using edgy? and is it i386 architecture?

---

### Post by tasukete on 2007-03-09
I am using UBuntu 6.10.
My PC's cpu is Intel Pentium4 2.6GHz, so i think i386.

---

### Post by PartisanEntity on 2007-03-09
You need to download 5 packages and copy them (perhaps through usb stick) to your laptop and install them. Then when you reboot network manager will make it very easy for you to find and connect to any wireless network, in your case your wep network.

The files you need are:

install these first:
[dhcdbd_1.14-2ubuntu2_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdhcdbd%2Fdhcdbd_1.14-2ubuntu2_i386.deb&md5sum=f597e9322731e08b68815383d274bac2&arch=i386&type=main")
[libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibn%2Flibnl%2Flibnl1-pre6_1.0~pre5%2Bsvn21-2ubuntu2_i386.deb&md5sum=0d836551f19893b6dbc34888b173d809&arch=i386&type=main")
[libnm-util0_0.6.3-2ubuntu6_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Flibnm-util0_0.6.3-2ubuntu6_i386.deb&md5sum=35f0369504c376261c6cddc76e29c64d&arch=i386&type=main")

then these:
[network-manager_0.6.3-2ubuntu6_i386.deb]("http://http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.3-2ubuntu6_i386.deb&md5sum=522cade5b931785517c0fb2bb7035a1e&arch=i386&type=main")
[network-manager-gnome_0.6.3-2ubuntu6_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.3-2ubuntu6_i386.deb&md5sum=1f857fb5abaa57675e4695baf66289b5&arch=i386&type=main")

Install then reboot, if you get an error message about cache then do this:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

And reboot again. Then network manager should work.

---

### Post by tasukete on 2007-03-09
i don't know how to install.
i did the file double click.
is it OK?

---

### Post by xyz on 2007-03-09
> **tasukete said:**
> i don't know how to install.
i did the file double click.
is it OK?
Take a look at this. Should help learn to install
[HOW TO INSTALL ANYTHING]("http://monkeyblog.org/ubuntu/installing/")

Good luck.

---

### Post by PartisanEntity on 2007-03-09
Double click each file and click on 'Install Package':

Here is a screen shot, in my case it says 'reinstall' because I have these packages already, in your case it should say 'install'. If you double click on it and it says 'reinstall' then you already have it and you can ignore it and move on to the next one.

---

### Post by tasukete on 2007-03-09
> xyz
thank you.
I lean how to install.

> PartisanEntity
I installed , and restart.
but I cannot do Internet.
so I try command "sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/" , and restart.
but I cannot do Internet.
:cry:

---

### Post by PartisanEntity on 2007-03-09
**Right click** on network manager and make sure 'Enable Wireless' is clicked.

Then **left click** on it and see if it lists wireless networks.

Screen shot attached:

---

### Post by tasukete on 2007-03-09
> PartisanEntity
I don't find the network manager.

---

### Post by PartisanEntity on 2007-03-09
This should be the one:

---

### Post by tasukete on 2007-03-09
I do right click it.
but what I see  is the mean of "A validation of network connection"  and  "information".
(These are activity.)
(Connection information is Non-activity)

---

### Post by PartisanEntity on 2007-03-09
I just noticed that in one of your earlier messages, when you posted the output of ndiswrapper -l, it listed 2 wireless cards. Do you have two wireless cards in your laptop?

Perhaps there is a conflict between the two.

Which drivers did you install using ndiswrapper?

Also please post the output of:

```
lspci | grep Broadcom\ Corporation
```

---

### Post by tasukete on 2007-03-09
I have two laptop PC.
One is a dual boot PC.(WIndows XP sp2 + ubuntu 6.10 japanese edition).
The another is Turbo Linux PC.
When I contribute comment to here, generally I use turbo linux.

Turbo Linux machine is use wireless LAN card, "Buffalo WLI-PCM-L11GP".
(I was able to use this card without my setting it on turbo linux.)
"Windows + ubuntu" machine is use wireless LAN card, "Buffalo WLI-CB-G54L".

my dualboot pc, in Windows, is no problem when i use wireless LAN.
but when i use ubuntu, i cannot use wireless LAN.



I think that I had better install ubuntu again.

---

### Post by tasukete on 2007-03-09
I did reinstall ubuntu.
How am I good from now on?

---

### Post by PartisanEntity on 2007-03-09
Well I was actually going to recommend that you try to uninstall one of the two drivers you had installed on your system, but that is too late now.

Since you have the BCM4306 chip in your wireless card I would recommend this [How To]("http://ubuntuforums.org/showthread.php?t=201902"), I have the same chip as you and this How To always works for me.

---

