---
title: "Resolution and Wifi"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by boogyman on 2006-10-02
Hey guys.
So I just installed ubuntu for the first time. Now I know basically nothing about it. I want to setup wifi so I can use internet and put my native resolution on. But have no idea how to do any.
I want 1680x1050 as my resolution and I use my internal wifi card to get an internet connection through my router.
Also if anyone has guides to help me get used to the system abit that would be great.
Bartman

---

### Post by Kobalt on 2006-10-02
Hello,

To change your resolution, open up a Console and type this command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as avaliable **with the spacebar**. Then restart X by pressing Ctrl+Alt+Backspace. Here you go ! 

To configure you WiFi card, we need the exact model of the card, to know which chip it uses. If you don't know that, you can find some useful information by typing this command line
```
lspci
```
Try finding the section of your WiFi card and copy/paste it here if you can.

To find help and guides, you can check out these for startance : 
[help.ubuntu.com]("http://help.ubuntu.com")
[Ubuntuguide]("http://ubuntuguide.org/wiki/Dapper")

Cheerio !

---

### Post by boogyman on 2006-10-02
Ok I got into the resolution thing and pressed space on the one i wanted, the tabbed to the done stop and spaced on that and got out of it but when I went to change my res the options were all the same.
Oh and with the lspci it came up saying

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev  03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714 5
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19 )
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapte r (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0000:0b:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

Can you understand that?
Thanks 
Bartman

---

### Post by Kobalt on 2006-10-02
Ok.
Did you restart well your Xserver with Ctrl+Alt+Backspace after you chose your resolution ? You only need to select the resolution with the space bar, after you've chosen it (once it has a * in front of it), you need to validate with Enter, not the space bar anymore. 

About your WiFi card, here is yours : 
> Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)

There are several guides on the forums about how to configure and get to work Broadcom cards (you will need to use a soft named Ndiswrapper). I don't know how to do that myself so I suggest you check out these HowTo. Post your questions from these threads if you need help, you'll get answers from people knowing the topic.
Here is a link to one thread on Broadcom cards : 
[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=howto+broadcom]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=howto+broadcom")

Here is were to get step by step installation guide for Ndiswrapper, if the previous link isn't helpful enough : 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

Cheerio !

---

