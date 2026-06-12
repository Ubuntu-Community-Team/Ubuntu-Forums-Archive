---
title: "How do I install ndisgtk?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by AI13 on 2007-12-17
Recently I became disenfranchised with windows, and as my mac is currently rejecting every os I send at it, I decided to convert to Ubuntu for my main computer. I ordered my cd, and a few weeks later it arrived. I let it sit for a few days, then popped it into my dvd drive bay, and restarted. When I saw the start up/install screen(not sure how it is commonly referred to), I chose the check disc for errors, seemed logical. After a few minutes of work, I got a message saying my 7.10 disc was free of errors, or something to that effect. So I installed. I had already set Ubuntu up in a dual boot before I had a disaster and my hard drive had been completely wiped, so I knew I would not be able to connect to the internet with out messing with some things. Here is where the problems start. I went to help, and as my access point uses windows drivers, I began looking for ndisgtk, except I could not find it, nor install it. I installed every packet that I could, but no ndisgtk. So, I go to the online help on the laptop that I am currently using, and I was instructed to look in the device manager to see if my computer even recognized my device anymore. 
So I fallowed the instructed path, and low and behold, no device manager. My first entery on the administration list is keyring. So, can someone please instruct me as to what has gone wrong, with either my self, or ubuntu. 
I would like to appoligize if this has already been asked, but I did not see it.Also, I apoligise if this is in the wrong thread.
Thank you.

---

### Post by mmb1 on 2007-12-17
When you say that keyring is the first thing in your admin list, do you mean it's the only thing listed?

---

### Post by Severun on 2007-12-17
I have been lucky enough to be able to have native support for the network cards I have used.   Someone please correct me if I'm wrong, but I think what you are looking for to run Windows NDIS stuff under linux is ndiswrapper...

BTW it would be helpful if you posted the problem in your subject, i.e. Having problem getting network card xxxxx to work.

Also include the model numbers of the things in question, i.e what network card are you using, what model number, what motherboard, main system, any other information about your setup would help.  It may be that with your card/model it is supported natively and you won't need to go through the ndis back bending.

---

### Post by AI13 on 2007-12-17
> **mmb1 said:**
> When you say that keyring is the first thing in your admin list, do you mean it's the only thing listed?

No, it is not the only thing listed, just the one on the top.

[QUOTE=Severun] I have been lucky enough to be able to have native support for the network cards I have used. Someone please correct me if I'm wrong, but I think what you are looking for to run Windows NDIS stuff under linux is ndiswrapper...

BTW it would be helpful if you posted the problem in your subject, i.e. Having problem getting network card xxxxx to work.

Also include the model numbers of the things in question, i.e what network card are you using, what model number, what motherboard, main system, any other information about your setup would help. It may be that with your card/model it is supported natively and you won't need to go through the ndis back bending[/QUOTE]

Yes, I did see somewhere that I had to use ndiswrapper, and your first paragraph is exactly what I am trying to do. Thank you for the advice, I will post my system info/ model #s soon, its a little late for me to do that. Also, thank you for the advice on Subject naming, I am a little new to forums so please forgive my ignorance.

---

### Post by mmb1 on 2007-12-17
Hmmm... this may not be my particular cup of tea, but I wish you luck, and I think that Severun may be able to find the solution to your problem.

---

### Post by Severun on 2007-12-18
> **AI13 said:**
> No, it is not the only thing listed, just the one on the top.



Yes, I did see somewhere that I had to use ndiswrapper, and your first paragraph is exactly what I am trying to do. Thank you for the advice, I will post my system info/ model #s soon, its a little late for me to do that. Also, thank you for the advice on Subject naming, I am a little new to forums so please forgive my ignorance.

I'm new to the Ubuntu community myself.  I'm finding out though at least here in the Ubuntu forums, the only stupid questions are the ones you don't ask.

We'll give you a hand if we can.

---

### Post by jfinkels on 2007-12-18
We need to know what kind of wireless card you have. To do this, type the following in the terminal (Applications > Accessories > Terminal):```
lspci -v
``` and post the output here. This will list all PCI devices connected to your computer, including your network controller (we're talking about wireless networking here, correct?). Then we can determine what kind of card you have and if you'll need ndiswrapper or some open source alternative (preferable).

---

### Post by AI13 on 2007-12-18
Its not a card, its a usb linksys receiver. Ill type that in though, and edit this for what I get when I get home.
 Thank you all for the help and the prompt responces.

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge 
        Subsystem: ASUSTeK Computer Inc. Unknown device 8118 
        Flags: bus master, 66MHz, medium devsel, latency 8 
        Memory at e0000000 (32-bit, prefetchable) [size=64M] 
        Capabilities: <access denied> 

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode]) 
        Flags: bus master, 66MHz, medium devsel, latency 0 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
        Memory behind bridge: e4000000-e6ffffff 
        Prefetchable memory behind bridge: d0000000-dfffffff 
        Capabilities: <access denied> 

00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS 
        Subsystem: Creative Labs Unknown device 100a 
        Flags: bus master, medium devsel, latency 32, IRQ 21 
        I/O ports at a000 [size=32] 
        Capabilities: <access denied> 

00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03) 
        Subsystem: Agere Systems Unknown device 044c 
        Flags: bus master, medium devsel, latency 32, IRQ 255 
        Memory at e7000000 (32-bit, non-prefetchable) [size=256] 
        I/O ports at a400 [size=8] 
        I/O ports at a800 [size=256] 
        Capabilities: <access denied> 

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI]) 
        Subsystem: ASUSTeK Computer Inc. A8V Deluxe or A8N-VM CSM Mainboard 
        Flags: bus master, medium devsel, latency 32, IRQ 16 
        Memory at e7001000 (32-bit, non-prefetchable) [size=2K] 
        I/O ports at ac00 [size=128] 
        Capabilities: <access denied> 

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V Deluxe/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 17 
        I/O ports at b000 [size=8] 
        I/O ports at b400 [size=4] 
        I/O ports at b800 [size=8] 
        I/O ports at bc00 [size=4] 
        I/O ports at c000 [size=16] 
        I/O ports at c400 [size=256] 
        Capabilities: <access denied> 

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 17 
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8] 
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1] 
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8] 
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1] 
        I/O ports at c800 [size=16] 
        Capabilities: <access denied> 

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 18 
        I/O ports at cc00 [size=32] 
        Capabilities: <access denied> 

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 18 
        I/O ports at d000 [size=32] 
        Capabilities: <access denied> 

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 18 
        I/O ports at d400 [size=32] 
        Capabilities: <access denied> 

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 18 
        I/O ports at d800 [size=32] 
        Capabilities: <access denied> 

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI]) 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, medium devsel, latency 32, IRQ 18 
        Memory at e7002000 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard 
        Flags: bus master, stepping, medium devsel, latency 0 
        Capabilities: <access denied> 

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
        Flags: medium devsel, IRQ 20 
        I/O ports at 1000 [size=256] 
        Capabilities: <access denied> 

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80) 
        Flags: medium devsel, IRQ 20 
        I/O ports at dc00 [size=256] 
        Capabilities: <access denied> 

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ff 
        Flags: bus master, medium devsel, latency 32, IRQ 19 
        I/O ports at e000 [size=256] 
        Memory at e7003000 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) (prog-if 00 [VGA]) 
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10 
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M] 
        Memory at d0000000 (32-bit, prefetchable) [size=256M] 
        Memory at e5000000 (32-bit, non-prefetchable) [size=16M] 
        [virtual] Expansion ROM at e6000000 [disabled] [size=128K] 
        Capabilities: <access denied> 

Thats what I get, do you need anything else?

---

### Post by hyper_ch on 2007-12-18
could yo rename the thread title to something more meaningful than a generic "need help"?

---

### Post by Rplus9 on 2007-12-18
I think I know what you are talking about,
I've got a Linksys USB wireless "thingy" and it's usually the source of my linux troubles.

ndisgtk is the gui face of ndiswrapper

if you don't have ndiswrapper installed
(check this by typing ndiswrapper in the command line)

you can add it through the package manager (the name escapes me) just search for ndiswrapper, grab both (the gtk might be listed but you need to download it, and if you don't have a wire connected you'll have to do without)

ndiswrapper installed, you need the key driver files.  If you have the same/similar device that I have then on the CD you'll be able to search for a .inf file.  unfortunatly that's not all you need, there are two .sys files, I don't have my notes right now but I can give you the names of those too (if you have the same card) 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
if you can find your device in the list it will tell you what you need file wise.

When I first cracked this, I had to actually bust open the .cab files and find the hidden .sys files I required... I made sure to make copies of those.

cutting to the chase, if you have the files then it should be quick after that

ndiswrapper wusb54gsc.inf (or whatever your .inf is called)

$ sudo cp *.sys /etc/ndiswrapper/wusb54gsc (again or whatever your .inf was called w/o the .inf part)
now your /etc/ndiswrapper/wusb54gsc folder should have all the files from the list.

$ ndiswrapper -l 
shows your device, if it's present and anomally free, continue, if it has errors or not present then you havn't got the correct files... keep looking

$ ndiswrapper -m
this writes a file to /etc/modprobe.d/ called ndiswrapper with the alias for your device, from what I understand this lets modprobe know what you're talking about.

$ modprobe -n ndiswrapper
the -n is a "dry run" to test, if you don't get any errors then you're good to go, if you did get errors, well at least you didn't really do anything.
right now I'm dealing with errors at this point so I can't help to much with problems here

$ modprobe ndiswrapper
doing it for real this time
$ dmesg | grep ndiswrapper
this is a nice to know, it shows you what you just did.

now go back and fiddle with your network manager and see if it works.

---

### Post by aysiu on 2007-12-18
From whatever computer you have connected to the internet, download these files:
[http://mirrors.kernel.org/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb)
[http://ftp.cs.umn.edu/pub/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
[http://lug.mtu.edu/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://lug.mtu.edu/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)

Transfer them to the desktop of Ubuntu however you can (USB stick?)

Then type this in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *.deb
``` That should install *ndisgtk*

---

### Post by AI13 on 2007-12-18
I got the first and last file fine, the middle one dosen't work though.

---

### Post by aysiu on 2007-12-18
> **AI13 said:**
> I got the first and last file fine, the middle one dosen't work though.
Pick another mirror from this list, then:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb&md5sum=832e3c942956e88a37ebf41e9a435b13&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb&md5sum=832e3c942956e88a37ebf41e9a435b13&arch=i386&type=main)

---

### Post by AI13 on 2007-12-18
Thank you very much. ndisgtk installed, and I found the .inf(i think thats what they are called) files, selected them for install, and now they are installed. Now, what do I have to do?

---

### Post by jfinkels on 2007-12-18
By the way, have you taken a look at this page? [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) and this one, too [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). It has info on many common wireless adapters.

As for my previous post, instead of typing "lspci -v", you will need to type ```
lsusb
``` or more verbosely:```
lsusb -v
```That will tell you info about all USB devices attached to your system.

Hopefully your wireless network adapter should work if you installed the Windows drivers (.inf files) using ndisgtk. To view all wireless extensions connected to your computer, type the following in the terminal:```
iwconfig
``` There should be one entry that doesn't say "no wireless extensions". That's the name of your wireless adapter (might be "eth1" or "wlan0" or "ath0" or something like those). To view the configuration of all your network adapters, wired and wireless, type the following in the terminal:```
ifconfig
```

Now, if it looks like your wireless adapter is still not working, post the output of "lsusb" and tell us what the device is so we can take a look at it.

---

### Post by AI13 on 2007-12-18
Thank you, those helped, everything is on and I am typing this from my Ubuntu comp. Thank you, this has been immensely help full. By the way, is there anywhere that I can go for advice on wine, and terminal commands?

---

### Post by jfinkels on 2007-12-18
> **AI13 said:**
> Thank you, those helped, everything is on and I am typing this from my Ubuntu comp. Thank you, this has been immensely help full. By the way, is there anywhere that I can go for advice on wine, and terminal commands?

Great! I'm glad you got your wireless connection to work.

Wine questions go here: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
or look around the official website here: [http://www.winehq.org/](http://www.winehq.org/)
or take a look at this: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

This website seems to be a pretty popular one as far as introductory command line lessons go: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Further introductory information is in my signature, I recommend taking a look at all of it, especially the first link on installing software, and aysiu's tutorials (the very same aysiu who posted above) at psychocats.net.

---

### Post by AI13 on 2007-12-18
Thanks, I look forward to working with Liniux

---

### Post by AI13 on 2007-12-25
Update:

Still working fine, had a hiccup or two, but its great now, thanks.

---

