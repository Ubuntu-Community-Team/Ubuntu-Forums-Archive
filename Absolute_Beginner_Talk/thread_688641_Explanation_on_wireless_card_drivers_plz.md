---
title: "Explanation on wireless card drivers plz?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by uruk912 on 2008-02-05
Ok I posted before about this and no one has fully answerd my question. Im trying to install madwifi-0.9.3.3 and i follow the guide all the way and it still dose not work can some one dumb it down for me? i dont want to go back to Windows but i might because it will recognise my wireless card but Linux is better in so many dif ways so some one help me out here.

---

### Post by spiderbatdad on 2008-02-05
could you post a link to the guide you followed and explain where it stops working?

---

### Post by gn2 on 2008-02-05
Also, what card do you have, make/model/chipset?

---

### Post by uruk912 on 2008-02-05
Ok sorry didnt explaint it all the way its saying in the restricted drivers it has Atheros Hardware Acess Layer (HAL) and ive been using this guide:
[www.madwifi.org/wiki/UserDocs/FirstTimeHowTo](www.madwifi.org/wiki/UserDocs/FirstTimeHowTo) 
And i was using a guide on here but i forget it

---

### Post by uruk912 on 2008-02-05
Oh and i get this error Module wlan is in use i know wlan is wireless but its not making no sense

---

### Post by ugm6hr on 2008-02-05
Sorry for questioning you - but I have been down this road before.

Why do you need to install madwifi 0.9.3.3?

The "Restricted Drivers" in Ubuntu includes a fairly up-to-date madwifi.

This is a moreuseful explanation: [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

After following the advice here, it should work.  But check that you need it first!

---

### Post by uruk912 on 2008-02-06
I did check everything i am just lost with it and i dont rlly want to go back to xp so thats why i ask so ill give it a try again.

---

### Post by ugm6hr on 2008-02-06
> **uruk912 said:**
> I did check everything i am just lost with it and i dont rlly want to go back to xp so thats why i ask so ill give it a try again.

If you are lost... Why not let us confirm some info?

```
lspci
lshw -C network
```

---

### Post by uruk912 on 2008-02-06
How do i replace or rewright the linux-restricted-modules-common file it wont let me.

---

### Post by uruk912 on 2008-02-06
uruk912@uruk912-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
uruk912@uruk912-laptop:~$ sudo lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

uruk912@uruk912-laptop:~$

---

### Post by Ex-windows on 2008-02-06
The "C" needs 2 b Capitol


uruk912@uruk912-laptop:~$ sudo lshw -c network

 sudo lshw -C network

---

### Post by ugm6hr on 2008-02-06
This may be your problem: [http://ubuntuforums.org/showthread.php?p=4259805#post4259805](http://ubuntuforums.org/showthread.php?p=4259805#post4259805)

> 06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapte

It appears this can be made to work - but it is not straight-forward.

---

### Post by uruk912 on 2008-02-06
uruk912@uruk912-laptop:~$ sudo lshw -C network
[sudo] password for uruk912:
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:5e:d2:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.1.46 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

---

### Post by uruk912 on 2008-02-06
Ok well i was reading what i posted above and it sees it witch it good but i tryed replacing the linux restricted thing and adding it with the new thing ath_something and it saids i cant because im not owner how to i get past this?

---

### Post by Ex-windows on 2008-02-06
OK first off sorry 2 post twice. I tried to multi qoute but It wouldn't work.
I have the same card. and this link
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
Says the madwifi thing should "just work" but it doesn't lol
And this thread
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
Says that if your   lshw -C network   shows the device as "unclaimed" you need to install the driver.
Which my lshw -C network shows the device as "unclaimed"

I even tried to install kwifi manager but got a "Cant open" error..
Any help would be greatly GREATLY appreciated..


EDIT
 Just saw the post on the atheros issues WOW this is really going to be tuff

---

### Post by ugm6hr on 2008-02-06
> **Ex-windows said:**
> OK first off sorry 2 post twice. I tried to multi qoute but It wouldn't work.
I have the same card. and this link
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
Says the madwifi thing should "just work" but it doesn't lol
And this thread
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
Says that if your   lshw -C network   shows the device as "unclaimed" you need to install the driver.
Which my lshw -C network shows the device as "unclaimed"

I even tried to install kwifi manager but got a "Cant open" error..
Any help would be greatly GREATLY appreciated..

See the link in my post above.  It links to a few other posts which explain why the first link doesn't work.

---

### Post by uruk912 on 2008-02-06
> **uruk912 said:**
> Ok well i was reading what i posted above and it sees it witch it good but i tryed replacing the linux restricted thing and adding it with the new thing ath_something and it saids i cant because im not owner how to i get past this?

No answer to this question? i know i read both of them.

---

### Post by uruk912 on 2008-02-06
Found out it my self on the question above

---

### Post by uruk912 on 2008-02-06
Well i assume that no one is looking any more but i will still post something new i tryed. i tryed using ndiswrapper and i did everything but it still dose not work any ideas?

---

### Post by uruk912 on 2008-02-06
PROBLEM SOLVED THANKS SO MUCH TO ANYONE WHO HELPED!!!!!!!!!!!!!!!!!!! Madwifi didnt work so i used ndiswrapper and it worked after i found out that linux misreads the wireless card driver it said AR5006EG but its actualy AR5007EG so yeah i got it to work thanks again everyone now i dont have to go back to winodws lol thanks thanks thanks....

---

### Post by Ex-windows on 2008-02-07
> **uruk912 said:**
> PROBLEM SOLVED THANKS SO MUCH TO ANYONE WHO HELPED!!!!!!!!!!!!!!!!!!! Madwifi didnt work so i used ndiswrapper and it worked after i found out that linux misreads the wireless card driver it said AR5006EG but its actualy AR5007EG so yeah i got it to work thanks again everyone now i dont have to go back to winodws lol thanks thanks thanks....
 How did you find that out????

---

### Post by ugm6hr on 2008-02-07
> **Ex-windows said:**
> How did you find that out????

Did you read any of the links from my post?

[http://ubuntuforums.org/showthread.php?p=4259805#post4259805](http://ubuntuforums.org/showthread.php?p=4259805#post4259805)
> It appears Linux identifies the AR5007EG as 5006EG. That is probably the problem.

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html](http://home.nyc.rr.com/computertaijutsu/rhwireless.html)
> Running lspci will probably list the card as 5006EG. However if there is a sticker on the bottom of the laptop saying Atheros AR5BXB63 the chances are that you have the 5007EG. If Windows is installed, you can also check with the Windows Device Manager which correctly identifies the card.

---

### Post by Ex-windows on 2008-02-07
> **ugm6hr said:**
> Did you read any of the links from my post?

[http://ubuntuforums.org/showthread.php?p=4259805#post4259805](http://ubuntuforums.org/showthread.php?p=4259805#post4259805)


[http://home.nyc.rr.com/computertaijutsu/rhwireless.html](http://home.nyc.rr.com/computertaijutsu/rhwireless.html)
 I guess I worded it wrong. I meant how he found out for sure what version he had ( ie checked  product info that came with comp or the Manufacturer site). . As in perhaps I may have a 5008 or 5005 or something. Anyway it is mute now becasue u were right about the windows side recognizing the card as a 5007. Yes, I have checked the links and hopefully  start tackling this later tonite.  Again I thank you for the info and the hard work putting that together.
:)

---

### Post by Ex-windows on 2008-02-09
> **Ex-windows said:**
> I guess I worded it wrong. I meant how he found out for sure what version he had ( ie checked  product info that came with comp or the Manufacturer site). . As in perhaps I may have a 5008 or 5005 or something. Anyway it is mute now becasue u were right about the windows side recognizing the card as a 5007. Yes, I have checked the links and hopefully  start tackling this later tonite.  Again I thank you for the info and the hard work putting that together.
:)

Although I haven't got it right just yet I am curious as to IF this ndis thingwill work on fiesty?
If I have to do some configuring I may as well have the os I prefer.And in this case I think I would prfer to  go with Ubunut Fiesty or Kubuntu Fiesty.
 Another q??
Where is the Network manager supposed to be? Synaptic says it is installed but I went all thru the System>admin>.main menu and dont see it Nor is it in Applications>internet.
Any suggestions would be greatly appreciated

---

### Post by ugm6hr on 2008-02-09
> **Ex-windows said:**
> Although I haven't got it right just yet I am curious as to IF this ndis thingwill work on fiesty?
If I have to do some configuring I may as well have the os I prefer.And in this case I think I would prfer to  go with Ubunut Fiesty or Kubuntu Fiesty.
 Another q??
Where is the Network manager supposed to be? Synaptic says it is installed but I went all thru the System>admin>.main menu and dont see it Nor is it in Applications>internet.
Any suggestions would be greatly appreciated

If you use Feisty, you will have to compile ndiswrapper yourself, since the ndiswrapper in the Feisty repository was not 100% reliable.  Gutsy does not have this problem.

Network Manager is default installed with Ubuntu,  It appears as the networking icon in the top right corner (in system tray).  It often looks like a picture of 2 computers, or if on wifi, as 4 bars (grey-blue).  Just left-click on the icon to bring up options:

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

---

### Post by Ex-windows on 2008-02-09
> **ugm6hr said:**
> If you use Feisty, you will have to compile ndiswrapper yourself, since the ndiswrapper in the Feisty repository was not 100% reliable.  Gutsy does not have this problem.

Network Manager is default installed with Ubuntu,  It appears as the networking icon in the top right corner (in system tray).  It often looks like a picture of 2 computers, or if on wifi, as 4 bars (grey-blue).  Just left-click on the icon to bring up options:

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

Well so much for that idea lol.. I have a hard enuff time compiling a list .:lolflag:

I have the cute lil comp screens so Thats good news however they only show the "wired" connection, so that's bad news I have followed all the instructions on this page
[http://ubuntuforums.org/showthread.php?t=649019](http://ubuntuforums.org/showthread.php?t=649019). I started with the 5006 eg. Then tried the 5007 but windows driver manager would not install that so I will try the 5007eg next. Would I need to re run all the command line info with each driver?
Thanks

---

### Post by ugm6hr on 2008-02-09
> **Ex-windows said:**
> Would I need to re run all the command line info with each driver?
Thanks

You have to re-enter these commands:
```

ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

I would also recommend you use the commandline to choose each driver (instead of using the "Windows Wireles Drivers" GUI tool:
```
sudo ndiswrapper -i ~/drivername.inf
```
Make sure the unpacked driver (.inf and .sys files) is in /home/username (i.e. your home directory) before doing this.

Then run the above commands again.

---

### Post by Ex-windows on 2008-02-09
Thanks again 
I will retry all of this tonite.

---

