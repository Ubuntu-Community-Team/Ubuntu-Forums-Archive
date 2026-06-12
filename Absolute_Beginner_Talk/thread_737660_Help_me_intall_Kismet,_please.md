---
title: "Help me intall Kismet, please"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by cmdowns on 2008-03-27
I'm totally new to linux. I've been running Ubuntu for about three weeks now. I've installed it on a hp pavillion laptop in a dual boot configuration along with XP. I am intersted in learning more about wireless netwoking, which is why I want to install Kismet.

From best I can tell, Kismet has been downloaded to my machine. I don't remember precisely how I did this, but it is listed in my home dir. If I cd into the dir named kismet, the subdir is called kismet-2007-10-R1, which I assume indicates the version of Kismet.

I tried to install Kismet using the script "sudo apt-get install kismet", which I found here in the forums. It really seemed like it wanted to install, but I end up getting the following (and I apologized for the wholesale cut and paste, but I didn't know what was and wasn't relevant):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libadns1 libgmp3c2 wireshark-common
Suggested packages:
  sox festival gpsd
Recommended packages:
  libadns1-bin wireshark tshark
The following NEW packages will be installed:
  kismet libadns1 libgmp3c2 wireshark-common
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After unpacking 36.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libgmp3c2 libadns1 wireshark-common kismet
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libgmp3c2 2:4.2.1+dfsg-5ubuntu4
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libadns1 1.4-0.1build1
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe wireshark-common 0.99.6rel-3
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe kismet 2007-01-R1b-1.1
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/adns/libadns1_1.4-0.1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/adns/libadns1_1.4-0.1build1_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/wireshark-common_0.99.6rel-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/wireshark-common_0.99.6rel-3_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/k/kismet/kismet_2007-01-R1b-1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/k/kismet/kismet_2007-01-R1b-1.1_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

If anyone could point me in the right direction, I sure nuff would be much obliged.

---

### Post by wormser on 2008-03-27
Make sure you have the repositories open.  System> Administration> Software Sources.  Enable Main, Universe, Multiverse and uncheck CD-rom.  I think your problem is the download server.  Change the download server on the drop down.  Then run:

```
sudo apt-get update
```

```
sudo apt-get install kismet
```

Then you have to edit the Kismet.conf file for your card.  Post the results of your card from:

```
lspci
```

If changing the download server does not work this might be a different issue and we can go from there.

---

### Post by cmdowns on 2008-03-27
Okay, that wasn't too painful. And I guess you were right about the download server. Once I changed that, everything seemed to fall in place. The results from lspci:

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

And thanks for the help.

---

### Post by wormser on 2008-03-27
> 02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

That is the wireless card.  I do not think Kismet has support for Broadcom cards.  You need to search the forums and net for Kismet support with that card.  If it does work you need to edit the kismet.conf file.

```
gksudo gedit /etc/kismet/kismet.conf
```

Search for the line # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE and change the line below it to the recommend settings for your card.

---

### Post by cmdowns on 2008-03-27
Okay, will do. And thanks again for the help. Yippeeee. . .adventures with Linux!

---

