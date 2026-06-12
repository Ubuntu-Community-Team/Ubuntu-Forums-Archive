---
title: "help in installing ubuntu 10.04 on Powerbook G4"
date: 2010-08-23
forum: Apple Hardware Users
---

### Post by linuxway on 2010-08-23
I was trying to install Ubuntu 10.04 on my powerbook g4  500 MHz, 512 RAM and I after it booted from cd and the word Install appeared I hit enter then the screen goes black or streaks of different colors. I tried Fedora 12 and I faced the same problem after I hit enter to install, again the screen went black.

Can you ppl help me install Ubuntu on powerbook g4, plz?

---

### Post by shawnhcorey on 2010-08-23
Do you see the boot message?  It looks something like this:

```
Welcome to Xubuntu 10.04 LTS (Lucid Lynx)!

This is a Xubuntu live CDROM,
built on 20100428.

The default option is 'live'.

If the system fails to boot at all (the typical
symptom is a white screen which doesn't go away),
use 'live video=ofonly'.

Press the tab key for a list of options, or type
'help' for help.

************************************
If in doubt, just press Enter, and if that
doesn't work, type 'live video=ofonly'.
************************************

```

---

### Post by linuxway on 2010-08-24
yes. I could see the boot message. The problems happens when I press the enter key to install. Maybe this is because of the display driver or something. I don't know. At first I thought that problem was due to faulty iso image but i sum-checked it and it turned out to be ok. I burned the image a speed of 4. but that didn't work. I downloaded Fedora 12 ppc and I got the same problem, the machine boots from the cd or dvd, starts to read and collects data, asks me to press enter to install and once I reach this point the screen turns gradually from light gray into black or mix of different colors . 

Thank you for your concern. I hope you can help me out.

---

### Post by linuxopjemac on 2010-08-24
do an installation without GUI. Your problem resides in a faulty xorg.conf (or a missing one). I would do a netinstallation:
[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

We can make you a working xorg.conf file later:
[http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128](http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128)

---

### Post by linuxway on 2010-08-24
> **linuxopjemac said:**
> do an installation without GUI. Your problem resides in a faulty xorg.conf (or a missing one). I would do a netinstallation:
[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

We can make you a working xorg.conf file later:
[http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128](http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128)


I tried mini.iso but at the stage when it asks me to configure the network connection, the connection fails. and it says that either i gave wrong info or there is something wrong with the network card yet the internet is working on Mac os and the IP's i gave were all correct.

Is there any way that I change the xorg.conf file before i burn the iso image, like it's location in the iso image so i can replace it with a working one.

I am new to linux world so i hope you can bear with me because if you ask me to do something and i would ask in details how i am going to do it or ask for a link that illustrates the whole topic. ;)

I really appreciate your help

---

### Post by linuxopjemac on 2010-08-24
If you do a netinstallation you have to connect an UTP card in your ethernet card. The cable has to be connected to your modem/router. If you try wireless, that could be problematic.

---

### Post by linuxway on 2010-08-24
> **linuxopjemac said:**
> If you do a netinstallation you have to connect an UTP card in your ethernet card. The cable has to be connected to your modem/router. If you try wireless, that could be problematic.

Yes, I connected the cable, I configured the network automatically and then manually but neither worked. I tried wireless it didn't work either.

---

### Post by shawnhcorey on 2010-08-24
If you have the same problem with both Ubuntu and Fedora, then your problem could be your video cable.  This is the second-most-common hardware problem with PowerBooks; the first being a busted hinge.

Turn the machine off and open the keyboard.  Get a small fan and blow air across the cooling fins inside.  After two minutes, restart the machine while still cooling it.  If it works correctly, then the problem is bad video cable.  A video cable cost about $80 USD and about $500 USD to install it.

---

### Post by linuxopjemac on 2010-08-24
I see. Well, then I would do an alternate install:
[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)

---

### Post by linuxway on 2010-08-25
Thank you all. 

shawnhcorey, I will try to do what you said and get back to you.But can the video cable be the problem while it works fine on Mac OS?!!!

linuxopjemac, can you send me a link for a detailed step by step installation guide for the alternate install as I've never done it before, plz?

---

### Post by linuxway on 2010-08-27
i downloaded the iso image again and burned it on cd not dvd. the cd reads slowly and now i am past that black screen. i can see ubuntu loading but after a while there is a message saying something like "kernel panic".

---

### Post by nisisb on 2010-08-28
I also encountered this situation! Really annoying!

---

### Post by linuxway on 2010-09-01
help plz. I am running mac os x 10.4.11 on my PB G4 and it's kind of slow and i can't watch videos seamlessly on youtube or any other flash sites.

---

### Post by shawnhcorey on 2010-09-01
> **linuxway said:**
> help plz. I am running mac os x 10.4.11 on my PB G4 and it's kind of slow and i can't watch videos seamlessly on youtube or any other flash sites.

Have you updated your kernel?  There's a bug in the kernel on the CD which makes it thrash the swap.  Since an update to the kernel came out today, you should update it as soon as possible.

---

### Post by linuxway on 2010-09-02
> **shawnhcorey said:**
> Have you updated your kernel?  There's a bug in the kernel on the CD which makes it thrash the swap.  Since an update to the kernel came out today, you should update it as soon as possible.

How can I do that,plz?

---

### Post by shawnhcorey on 2010-09-02
The easiest way is to update everything.  Go to System -> Administration -> Update Manager

When it's ready, click Check, the Install.

It might take a while; there have been a number of updates since April.

---

### Post by linuxway on 2010-09-03
> **shawnhcorey said:**
> The easiest way is to update everything.  Go to System -> Administration -> Update Manager

When it's ready, click Check, the Install.

It might take a while; there have been a number of updates since April.

Ubuntu is not installed on my laptop because I couldn't do that. So how can I update the kernel on the cd?

---

### Post by shawnhcorey on 2010-09-03
> **linuxway said:**
> Ubuntu is not installed on my laptop because I couldn't do that. So how can I update the kernel on the cd?

You can't.  You have to get the latest version of the kernel from the web.

---

### Post by linuxway on 2010-09-03
> **shawnhcorey said:**
> You can't.  You have to get the latest version of the kernel from the web.

Can you give the link to the new kernel and how I can add it to the image before i burn it to a cd?

---

### Post by linuxway on 2010-09-08
> **linuxopjemac said:**
> I see. Well, then I would do an alternate install:
[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)

on booting from the alternate cd I get the following error message:

yaboot.conf: Unknown or corrupt filesystem 
Can't open config file
boot:

I burned the cd with the speed of 4x.

Any suggestions?

---

### Post by linuxopjemac on 2010-09-08
I don't know why you have these problems. I would install Debian Linux though.

---

### Post by linuxway on 2010-09-08
> **linuxopjemac said:**
> I don't know why you have these problems. I would install Debian Linux though.

I tried to install Debian but I couldn't connect to the internet. By the way the connection was wired. Besides I am not that experienced. I have never installed Linux through command line. I began to give up :(

---

### Post by linuxopjemac on 2010-09-08
Just follow my tutorial:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

or the tutorial by Oswald:
[http://forums.debian.net/viewtopic.php?t=20481](http://forums.debian.net/viewtopic.php?t=20481)

For X you need to consult me later.

---

### Post by linuxway on 2010-09-08
> **linuxopjemac said:**
> Just follow my tutorial:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

or the tutorial by Oswald:
[http://forums.debian.net/viewtopic.php?t=20481](http://forums.debian.net/viewtopic.php?t=20481)

For X you need to consult me later.

Thank you so much for your help. I am going to try again and tell you what would happen.

---

### Post by linuxway on 2010-09-10
> **linuxopjemac said:**
> do an installation without GUI. Your problem resides in a faulty xorg.conf (or a missing one). I would do a netinstallation:
[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

We can make you a working xorg.conf file later:
[http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128](http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128)


I managed to install ubuntu 10.04. I chose something like "live video=ofonly" but the screen is like a negative and I got the message "ubuntu is running on low graphices mode". So how can I fix this problem and how can I use that xorg.conf file? 

Thanks in advance

---

### Post by Chipmunkor on 2010-09-10
try using "live video=ofonly" instead of hitting enter?

---

### Post by linuxway on 2010-09-11
> **Chipmunkor said:**
> try using "live video=ofonly" instead of hitting enter?

I typed "live video = ofonly" and the installation went on but I could barely see the what was written on the screen. Thanks to my previous installations on intel-based pc's I was able to follow the installation though the words was barely readable as the the colors were the wrong ones and the text was hard to read. The screen was like a negative photographic film.

---

### Post by linuxway on 2010-09-12
Today, I tried to install ubuntu 10.04 from the alternate cd. After two hour installation, a message showed up saying that couldnt install yaboot as there was no mac boot strap. knowing that i split the hard drive into 2 partition. the first partition i installed mac on it and the second one i was trying to install ubuntu on.

---

### Post by linuxopjemac on 2010-09-13
Oh man, I don't know why the Ubuntu installer does not do this well automatically. You have to make 3 partitions manually. A Apple bootstrap partition of 1Mb, the root partition (ext3) and the swap partition (same amount of RAM as your memory). In the bootstrap partition, the installer puts yaboot.

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by linuxway on 2010-09-16
I installed ubuntu 10.04 from alternate cd and the installation was complete then i rebooted. on startup and loading the kernel, the screen gets dark. so what to do?

---

### Post by linuxopjemac on 2010-09-16
What is your exact Mac model?
[http://everymac.com](http://everymac.com)

---

### Post by linuxway on 2010-09-18
> **linuxopjemac said:**
> What is your exact Mac model?
[http://everymac.com](http://everymac.com)


Machine Model:    PowerBook G4
  CPU Type:    PowerPC G4  (11.3)
  Number Of CPUs:    1
  CPU Speed:    500 MHz
  L2 Cache (per CPU):    1 MB
  Memory:    512 MB
  Bus Speed:    100 MHz
  Boot ROM Version:    4.1.8f5

PCI/AGP Cards:

TXN,PCI1211-00:

  Name:    cardbus
  Type:    cardbus
  Bus:    PCI
  Slot:    PC Card
  Vendor ID:    0x104c
  Device ID:    0xac1e
  Revision ID:    0x0000

ATY,RageM3:

  Type:    display
  Bus:    AGP
  VRAM (Total):    8 MB
  Vendor:    ATI (0x1002)
  Device ID:    0x4c46
  Revision ID:    0x0002
  ROM Revision:    113-XXXXX-119

Display:

  Type:    display
  Display Type:    LCD
  VRAM (In Use):    8 MB
  Resolution:    1152 x 768
  Depth:    32-bit Color
  Main Display:    Yes
  Mirror:    Off
  Built-In:    Yes
  Online:    Yes

ATY,RageM3p12B:

  Status:    No display connected




ATA:

ATA-4 Bus:

TOSHIBA MK2016GAP:

  Capacity:    18.63 GB
  Model:    TOSHIBA MK2016GAP
  Revision:    U0.31 A
  Serial Number:    61T41480T
  Removable Media:    No
  Detachable Drive:    No
  BSD Name:    disk0
  Protocol:    ATA
  Unit Number:    0
  Socket Type:    Internal
  OS9 Drivers:    No

Hard Drive 20GB:

  Capacity:    18.5 GB
  Available:    5.64 GB
  Writable:    Yes
  File System:    Journaled HFS+
  BSD Name:    disk0s3
  Mount Point:    /

ATA-3 Bus:

MATSHITADVD-ROM SR-8187:

  Model:    MATSHITADVD-ROM SR-8187
  Revision:    HA18
  Serial Number:    
  Drive Type:    CD-ROM/DVD-ROM
  Removable Media:    Yes
  Detachable Drive:    No
  Protocol:    ATAPI
  Unit Number:    0
  Socket Type:    Internal


linuxopjemac, thank you so much for your help.
Today, I installed Debian and i followed the steps you pointed out in the link you provided. the installation went ok till the moment when it says "install software" then i shut the laptop down because my connection was too slow and it would take me days to complete the installation, I turned the laptop on and I logged on debian as root and ran mint-installer but meanwhile, debian installed more packages other than mint lxde and kept downloading packages and installing them (gnome was one of those packages) for a long time. I shut it down again and after booting the got "Warning: Fake start-stop-daemon called. Doing nothing" I searched and fixed this problem and after rebooting again I was faced with the screen getting dark. I am really frustrated. Fedora 12 didnt work. Ubuntu 10.04 alternate cd didnt work. ubuntu 10.04 live cd worked to some extent at least i could log into ubuntu but the GUI was like a negative photographic film and it was hard to ready anything. 
So what do you suggest?

---

### Post by linuxopjemac on 2010-09-18
For my Linux Mint you need a fast internet connection indeed. You have to finish everything, you cannot just stop in between. It has to download all packages and install them. I would just try again and be more patient. Don't reboot just follow the instructions. If you are finished with everything in the command line, you don't reboot yet but you contact me.

There is a guy on this forum who installed it on 16 G3/G4 machines:
[http://ubuntuforums.org/showthread.php?t=1576658](http://ubuntuforums.org/showthread.php?t=1576658)

BTW If you have a working system now (it installed everything), you can do the following:

boot like this:

```
Linux 1
```

This will bring you in single user mode.

Then:

```
wget http://mac.linux.be/files/xorg/powerbook8.txt
sudo mv powerbook8.txt /etc/X11/xorg.conf
```

reboot and enjoy X.

---

### Post by linuxway on 2010-09-19
I installed Debian and let the installation complete without any stops and there was no problems during installation and but during the installation, the installer installed gnome. After finishing the installation, the system rebooted, the system was reading some lines and something like " starting abstraction layer" and "starting gdm" and again the screen got dark. Then I tried to get on single user mode and i got "Will now switch to single-user mode. INIT: Going single user. INIT: Sending processes the TERM signal *error*: '*single*' *exited outside the expected code  flow*." and asked me for root password to do maintenance. I typed my root password and the user was something like "debian#" then 
I did 
wget [http://mac.linux.be/files/xorg/powerbook8.txt](http://mac.linux.be/files/xorg/powerbook8.txt)
sudo mv powerbook8.txt /etc/X11/xorg.conf

I got confirmation line that the download was complete but after hitting the second line no confirmation line showed, I was back to "debian#". Then rebooted and the same black screen.

---

### Post by linuxopjemac on 2010-09-19
You can also try to boot normally and then when you see theblack screen hit

CTRL-ALT-F1

login and do the xorg.conf trick

---

### Post by linuxway on 2010-09-19
> **linuxopjemac said:**
> You can also try to boot normally and then when you see theblack screen hit

CTRL-ALT-F1

login and do the xorg.conf trick


linuxopjemac, you made my day. It worked like magic. and another happy user. thank you so much for your great help. You have no idea how happy I am. I have been searching for a solution for this problem for months. Thank you again and I wish you the very best. BTW I am writing this on debian on my powerbook G4 :)

---

### Post by linuxopjemac on 2010-09-19
So now it's time to mintify it ? ;)

---

### Post by linuxway on 2010-09-20
> **linuxopjemac said:**
> So now it's time to mintify it ? ;)

Yes, I will install Mint lxde desktop later but right now I have problems with right click as you know that model track pad doesn't have right click. Another problem is screen brightness, the brightness is at max but it still looks a lil bit gloomy.

---

### Post by linuxopjemac on 2010-09-20
install mouseemu
```
sudo apt-get install mouseemu
```

you will have right click with F11

screen brightness:
```
sudo apt-get install pbbuttonsd
```

Fn F3/F4 I think adjusts then

---

### Post by linuxway on 2010-09-23
> **linuxopjemac said:**
> install mouseemu
```
sudo apt-get install mouseemu
```you will have right click with F11

screen brightness:
```
sudo apt-get install pbbuttonsd
```Fn F3/F4 I think adjusts then


it's working now. but the maximum degree of screen brightness isn't that bright. Are there some parameters or values that I can change to get the brightest degree?

---

### Post by linuxopjemac on 2010-09-23
I am not familiar with that. Read the documentation of pbbuttonsd is my advize. It should also be possible to set the brightness via the terminal.

---

