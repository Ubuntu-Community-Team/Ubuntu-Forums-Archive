---
title: "Frustrated newbie 'Wireless'"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Sunnyboyuk on 2008-02-03
I'm a complete novice at this stuff [typing on my trusty XP box]

I'm really keen to use Ubuntu on an old laptop that I have so that I can learn the ropes and set-up an old PC for my daughter.

I have a wireless network that I work off and have bought an EDIMAX wireless lan USB adapter.  How do I get the drivers on to get it working?

Please can someone point me in the right direction [please bear in mind I'm a non-techi from the windows side of the street trying to move??]

Cheers :confused:

---

### Post by Alx c on 2008-02-03
Go here [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) (you need to plug in the usb adapter first)

---

### Post by Sunnyboyuk on 2008-02-03
Many thanks for the link its great !

How do I load a device driver as it is spotting the usb device but there doesn't seem to be a driver installed [is there a link about that?]

Thanks again

---

### Post by jan quark on 2008-02-03
look in 

system > administration > restricted dirvers manager

if there is some inactive driver


perhaps your device is supported out-of-the-box
and you do not need to install any additional drivers

pls post also the resutlt fo the following terminal commands

```
iwconfig
```

```
lspci
```

```
lshw -C network
```

```
sudo iwlist scan 
```

---

### Post by Sunnyboyuk on 2008-02-03
Thanks 

PLEASE fogive me if its wrong !!  This is like Russian to me ??  

Code:iwconfig

lo    no wireless extensions.
irda0   no wireless extensions.

wmaster0   IEEE 802.11g    Frequency:2.412  Ghz
                   RTS thr:off       Fragment thr=2346 B

wlan0         IEEE 802.11g    ESSID:""
                  Mode;Managed  Frequency:2.412 GHz  Access Point: Not-Associated
                  RTS  thr:off       fragment thr=2346 B

Code:lspci

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:06.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:06.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:06.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:06.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:07.0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)



Code:lshw -C network

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:2e:bd:5b:0b
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g



Code: sudo iwlist scan

lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     Interface doesn't support scanning : Network is down

---

### Post by Sunnyboyuk on 2008-02-03
BTW - I have no restricted drivers manager?

Is that a problem?

---

### Post by iammeagain on 2008-02-03
> **Sunnyboyuk said:**
> BTW - I have no restricted drivers manager?

Is that a problem?

You should  be able to install the restricted drivers manager using Synaptic. Just search for restricted-manager 
I wish I could help more, but I'm searching around because of my own wireless problem.

---

### Post by Sunnyboyuk on 2008-02-03
Flipin hell this is complex I can see why is a fringe activity ?

I need to install the driver and appear to have no easy compiler Synaptic is not supported on my machine apparently.

I have got the driver pack on my desktop 

2008_0117_RT73_Linux_STA_Drv1.1.0.0

I am now officially lost and wondering why ?? but I'm sure its all worth it to get over my MS reliance eh??

PLEASE PLEASE help before I skip the bloomin box......

---

### Post by billgoldberg on 2008-02-03
Synaptic is not supported?

That can't be right.

I see you're using dapper, wich is an old (lts, but still) version of ubuntu.

Anyhow.

Some wireless adapter aren't fully supported by ubuntu (the manufactures don't make the drivers).

You can always use ndiswrapper to install the windows 2000/xp driver and use that in ubuntu, but it's a bit complicated.

Why don't you take a look at the supported wireless usb adapters and buy one of those.

link:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

---

### Post by Sunnyboyuk on 2008-02-03
Muchos grassy **** 

I will give it a go !!  Is it worth upgrading my Ubuntu instead to a better [or more up todate] version?

Thanks again, I really appreciate all this help, I'm sure that I will crack it

---

### Post by jan quark on 2008-02-03
upgrading no

but a fresh install of the newest version will surely help to minimize the wireless problems
the support for network devices has greatly improved 

download gutsy gibbon 7.10 from here

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Sunnyboyuk on 2008-02-04
Jan 

Have tried loading and get

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs)

any clues as to what I should do?

Many thanks :confused:

---

### Post by jan quark on 2008-02-04
sry if I dont understand but what do you have tried to load

I am myself fighting with my 64 bit system ... :) so I hope my laptop wont explode in the next few hours

but will try to help you..

did you downloaded the iso image and burned it correctly and already installed the new system ?

---

### Post by Sunnyboyuk on 2008-02-04
MMMmmm now thats a question ??  Gutsy Gibbon from the site that you directed me too, I have it in the CD drive and it runs then when I say install it pops that message up?

I think that I have downloaded it correctly  [and for back-up I have ordered a disk from the local Linux supplier !!] and I used ISO record which seemed to be fine?

Maybe its me ?  It looks fine at the start-up and offers me all the right choices and when it starts to load drops that lovely message up.

I'll wait for the postman and try that one!

I hope that all is well with your system

Many thanks again:)

---

### Post by dstew on 2008-02-04
You got this error when starting the Live CD, corrrect? That is, when you selected the "Start or Install Ubuntu" choice, right? The error occurred when the initial RAM file system (initramfs) tried to load the kernel. It encountered an error of some kind, and dropped out to its own command line. You probably won't be able to do anything useful from that command line. Usually this is a problem with the Live CD not interacting well with your hardware. It could be due to some flaw in the Live CD, so it is important to check integrity (other menu choice). Also, burning the Live CD at slow speed sometimes helps. But sometimes this happens with a perfect Live CD.

It is probably better to try to install Ubuntu using the Alternate Install CD. It installs the same Ubuntu system using a text-based installer that is more reliable.

---

### Post by Sunnyboyuk on 2008-02-04
I will try with a commercially purchased disc [ordered]
I'm really not bothered which version as long as it can support my IBM old laptop and the wireless USB dongle that I bought.
I just want to become mildly roasted!! ;)

---

### Post by ugm6hr on 2008-02-04
You need to find out what chipset your USB device has:

```
lsusb -v
```

USB wifi devices are a bit hit and miss in Linux.  Many require ndiswrapper to get them to work.  Gutsy may or may not be any better.

Edimax tend to use Realtek chipsets, which have reasonable Linux drivers.  You just have to find them!

---

### Post by Sunnyboyuk on 2008-02-07
Have upgraded to 7.1 and plugged in my Edimax Ubuntu compatable wireless usb dongle.  Still no joy !!  no restricted drivers.

Loosing the will to go on !!

I am stuck with untaring or something like that?  

apparently I have the driver and install disk with the ralink USB RT73 but I'm lost as to how to install??

Last ditch before I ditch 

Can anyone help?

:confused:

---

### Post by ugm6hr on 2008-02-08
Assuming you are correct about your chipset (you didn't post here):
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I believe there are some Linux distros with better out-of-the-box RT support than Ubuntu.  Not sure which though.
This suggests PCLinuxOS does a better job though: [http://linuxmint.com/forum/viewtopic.php?f=53&t=4262&p=27611&hilit=rt73#p27611](http://linuxmint.com/forum/viewtopic.php?f=53&t=4262&p=27611&hilit=rt73#p27611)

---

### Post by Sunnyboyuk on 2008-02-08
Many thanks again.

Mint looks like its the sort of thing a numpty like me needs ;@)

Cheers

---

### Post by stalkingwolf on 2008-02-08
This link might be of help.[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

---

### Post by ugm6hr on 2008-02-08
> **Sunnyboyuk said:**
> Mint looks like its the sort of thing a numpty like me needs ;@)

Perhaps - but you will have the same wifi problems as in Ubuntu.

PCLOS:[http://www.pclinuxos.com/](http://www.pclinuxos.com/)

---

### Post by Sunnyboyuk on 2008-02-08
Ah maybe its cheaper to buy a really long wire to run up the stairs?

Negotiations with other half begin tomorrow ;@)

Thanks again:lolflag:

---

### Post by Sunnyboyuk on 2008-02-15
guys i'm in with mint and all your help !

many thanks !!!!

:)

---

