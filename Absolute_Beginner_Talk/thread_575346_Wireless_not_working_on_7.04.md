---
title: "Wireless not working on 7.04?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by AlienTech on 2007-10-13
Okay please bear in mind that I am VERY new to the Linux world. I been researching my issue the past few days and here's what's up:

I  have a Linksys PCI Wireless card that doesn't seem to have a driver installed for it. (I say this, though I have no idea how I would check this.) My system is setup as a dual boot, hence my ability to be on-line now. Unfortunately I have absolutely no connection when I'm logged in Ubuntu. My research has brought me to many forums that discuss the issue.... but no one seems to ask : What do I Need? How do I install that manually? 

I can download everthing I may need while I'm in XP (like ndiswrapper) but I really need help Manually installing the programs/app's from my hdd....

Love everything else and my wired network set up just fine. 

Again, I've been pointing and clicking w/ windows up untill last week... so please be gentle. Thanks in advance

---

### Post by overdrank on 2007-10-13
> **AlienTech said:**
> Okay please bear in mind that I am VERY new to the Linux world. I been researching my issue the past few days and here's what's up:

I  have a Linksys PCI Wireless card that doesn't seem to have a driver installed for it. (I say this, though I have no idea how I would check this.) My system is setup as a dual boot, hence my ability to be on-line now. Unfortunately I have absolutely no connection when I'm logged in Ubuntu. My research has brought me to many forums that discuss the issue.... but no one seems to ask : What do I Need? How do I install that manually? 

I can download everthing I may need while I'm in XP (like ndiswrapper) but I really need help Manually installing the programs/app's from my hdd....

Love everything else and my wired network set up just fine. 

Again, I've been pointing and clicking w/ windows up untill last week... so please be gentle. Thanks in advance

Hi and welcome, if you have a wired connection in ubuntu please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by AlienTech on 2007-10-14
please don't mind the delay in response I had to boot up in Ubuntu then back here and I wasn't sure what I should use for the text so I used Notepad (windows) here ya go.....

paul@Alien:~$ lspci
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:12.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
04:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
04:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Hope this helps and thanks again

---

### Post by overdrank on 2007-10-14
> **AlienTech said:**
> please don't mind the delay in response I had to boot up in Ubuntu then back here and I wasn't sure what I should use for the text so I used Notepad (windows) here ya go.....

paul@Alien:~$ lspci
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:12.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
04:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
[COLOR="Red"]04:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]

Hope this helps and thanks again

Hi I have highlighted you wireless card and this link should help
[http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+Corporation+BCM4318)
Is your wired connection working in Ubuntu? I would be easier to install the wireless from with in ubuntu. Good luck!

---

### Post by AlienTech on 2007-10-14
This might be silly but does Ubuntu use a Gnome or KDE? Seems like the KDE option only has an online install via the "wget". (This is a wild guess assuming "wget" means web get) If it KDE, then I'm s.o.l.? 

I've downloaded the "offlie" installer for Gnome just in case i'm lucky... and yes my wired connection is working BUT wired has no internet just a LAN for my PC's. The Wireless Network is a shared Network. So I literally have NO INTERNET on Ubuntu


I Really appreciate any and all your help

---

### Post by strabes on 2007-10-14
Ubuntu uses gnome by default. I'd recommend [this howto](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) for a novice like yourself. It's really easy and has worked on both computers with that wireless chipset I've tried it on.

---

### Post by AlienTech on 2007-10-14
I've downloaded the files, coping them to storage and trying this out in Ubuntu.... Please give this thread a read in a few and see were I'm at.... I hope this finally works

---

### Post by AlienTech on 2007-10-14
Alright I tried the how to's for the offline post and I run into an error when trying to move the 3 d/l'd packages to the /var/cache/apt/archives.... Ubuntu says I don't have the authority to write there. Do I need to change somthing about my logon? I feel I'm getting closer to my goal of updating Ubuntu and adding beryl and such via my wireless connection.

I was able to move the 4th .exe file to my user account with no errors popping up

---

### Post by AlienTech on 2007-10-14
ok.... I've got the .tar files to the var/cache/apt/archives as suggested by the "offline" howto's. I now try the code:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 

No problems so far: THEN

sudo apt-get install ndiswrapper-utils-1.9 - but it says that "utils-1.9 couldn't be found" - it's in the proper directory as per the forum posted here: [http://ubuntuforums.org/showpost.php?p=3022036&postcount=21](http://ubuntuforums.org/showpost.php?p=3022036&postcount=21)

Now I'm stuck again.... PLEASE if you have any information that you think is helpful..... please let me know:

The exact error I don't know (switching between XP and Ubuntu has proven to be a royal pain in the ....

---

### Post by MatthewPlanchard on 2007-10-14
Connect to a wired connection and make sure your system is fully upgraded, as well.

---

### Post by AlienTech on 2007-10-14
Can't..... my pci network card is fried. My only option for online access is my wireless

---

### Post by AlienTech on 2007-10-14
Ok..... since I can't find anymore info about "offline installation" for everything I need such as NDISWrapper.... My only other thought is this:

If I were running XP (In which I can access the internet because The drivers for my wireless card load) is there someway to run Ubuntu (perhaps directly from the disc) and Utilize windows for Internet access? I know I need an update and I'm truly at wits end.

---

### Post by AlienTech on 2007-10-15
Well... 2 weeks... no internet.... no help forums seem to cover my issue.... this stinks. I really do love the idea of Linux and Ubuntu... but I'm asking one last time before I revert to XP:

I have ONLY a wireless connection for the net. No wired LAN (ethernet on motherboard is dead.) I have found the Windows drivers and Understand the concept of using NDISwrapper to apply the driver but I need an OFFLINE solution to install apps. I.E. where do a place the .tar files? What terminal prompt will install them from the HDD without using Wget? 

Doesn't seem to difficult in theory, but it's been two weeks almost abd I'm still forced to use XP or Vista.... ahhhhhhhhhhhhhhhhhh

I know I keep posting but I really want to use Ubuntu..... any and all help is greatly appreciated!

---

### Post by MatthewPlanchard on 2007-10-15
As far as I know, the only actual solution would be to go out and get some kind of mobile PCI LAN adapter. I think they sell them at Office Depot. It's like a wireless network card, except it's got a LAN port instead. Far as I know, there's no other way to get into the internet, although someone who's been here longer could probably say that with much more certainty than I.

---

### Post by AlienTech on 2007-10-16
Ty for the advice... I appreciate it. I would've never guess this to be an issue. I mean, after all. I simply want to install from the HDD instead of the net. Just seems very silly that I've spent all this time trying to do something that seems so very basic.  I thinking Ubuntu doesn't have a  driver for the LAN device you were mentioning as well, but I still very much appreciate yours and any feedback. I LOATHE WINDOWS.... but thats just me.



Linux is the revolution.... I wanna come too :(

---

