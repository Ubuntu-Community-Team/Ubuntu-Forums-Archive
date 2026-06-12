---
title: "Help with wireless router"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-08-04
Hi 
I am using Xubuntu, and would like to add a wireless router 
The Desktop is windows XP Adsl PPPoe, the laptop is Xubutu
the card is an I-O data card ( Airport ) ieee802.11g/b

The instruction that came with it are for indows XP, I have Never set up a router before 

I looked up on wiki but its all greek to me, Though NDSwrapper looked promising !

Can someone head me in the right direction!

Stephen

---

### Post by kb3hkg on 2006-08-04
Are you trying to make the Xubuntu machine into a router or just connect it wirelessly to one?

---

### Post by basilwatson on 2006-08-05
connect to one 

The desktop is the main machine (winxp) and this laptop is xubuntu and we just bought a broadband router, So I assume that the desktop is the main one and the laptop is the satalite one 

Its all designed for widows plug and play 

THOUGH in the cd provided there is a .bin file ... ( a token gesture for linux??~)

anyway Having never done this before and a completer newbie to linux ...whats the first thing ///

I have been reading , but my eyes glazed over and it got lost ..

I am trying that ndswrapper ..if i can find it !!!

Stephen

---

### Post by benuski on 2006-08-05
Could you type ```
lspci
``` into a terminal?  The last output should be "Network Controller", and paste what it says?  It will help us determine what how-to guide will be able to help you.

---

### Post by basilwatson on 2006-08-05
ok here it is 

s@s-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 03)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
0000:02:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
0000:02:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
s@s-laptop:~$

hope that helps 


Stephen 

lspci was that a souce list or something??

---

### Post by benuski on 2006-08-05
lspci lists all of your PCI devices... and I don't see your wireless card there... is it built in or an external plugin in card?

It may just be that I'm used to broadcom chipsets as opposed to IBM ones.

---

### Post by basilwatson on 2006-08-05
Sorry that took a bit of fluffing about 

It wouldnt connect to the net  with both the wired lan cable and the wireless card in there 

but here is the new updated lspci 
s@s-laptop:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 03)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
0000:02:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
0000:02:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
s@s-laptop:~$


Hope that is   btw its external pci card

Stephen

---

### Post by basilwatson on 2006-08-05
bump

---

### Post by basilwatson on 2006-08-05
Come on fella 

all I want to do is get the router working !

I have read every thing I could find For the last 6 hours 

I dont know what to do 

Everytime I try to do something, I post here,  have had a couple of helpful replys ,, but most of the time its 

Sorry your car dont work Mam , try reading the owners manual.... 

It really is an off putting experience to this whole thing 

Nice program but all I want to do is plug and play ,,,Not spend 6 hours trying to figure out something that A, I dont want to know , and B shouldnt have to 

Does you wife know how the car engine works ???? thought not 



PLEASE PLEASE I beg of ANYONE 


How can I get this router workin [COLOR="Black"]**WHAT DO I DO**[/COLOR] ??????????

below is all the info I managed to get .

I think there driver is there ( i am not sure )  but it needs an adress?? or some way of finding the router??


Sorry for the rant but  I hope you can ubderstand my feeling s

Kind regards 

Stephen

its a bit long sorry but I dont know what is relevant 
s@s-laptop:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 03)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
0000:02:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
0000:02:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
s@s-laptop:~$


s@s-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"default"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:B0:6F:92:5C
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/94  Signal level=-33 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:20   Missed beacon:6


s@s-laptop:~$ sudo iwconfig atho0 channel 6
Password:
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device atho0 ; No such device.
s@s-laptop:~$

s@s-laptop:~$ sudo lshw -businfo
Bus info     Device     Class       Description
===============================================
                        system      FMV8MR9LL7
                        bus         ACADIA
                        memory      BIOS
cpu@0                   processor   Pentium III (Coppermine)
                        memory      L1 cache
                        memory      L2 cache
                        memory      System Memory
                        memory      DIMM SDRAM Synchronous 100 MHz (10.0 ns)
                        memory      DIMM SDRAM Synchronous 100 MHz (10.0 ns)
pci@00:00.0             bridge      82815 815 Chipset Host Bridge and Memory Controller Hub
pci@00:01.0             bridge      82815 815 Chipset AGP Bridge
pci@01:00.0             display     Rage Mobility M4 AGP
pci@00:1e.0             bridge      82801 Mobile PCI Bridge
pci@02:08.0  eth0       network     82801BA/BAM/CA/CAM Ethernet Controller
pci@02:0a.0             bridge      OZ6933/711E1 CardBus/SmartCardBus Controller                        network
pci@02:0a.1             bridge      OZ6933/711E1 CardBus/SmartCardBus Controllerpci@00:1f.0             bridge      82801BAM ISA Bridge (LPC)
pci@00:1f.1             storage     82801BAM IDE U100
ide@0        ide0       bus         IDE Channel 0
ide@0.0      /dev/hda   disk        FUJITSU MHR2020AT
ide@0.0,1    /dev/hda1  disk        Linux filesystem partition
ide@0.0,2    /dev/hda2  disk        Extended partition
ide@1        ide1       bus         IDE Channel 1
ide@1.0      /dev/hdc   disk        CD-224E
             /dev/hdc   disk
                        disk        Apple partition map
                        disk        Apple HFS
pci@00:1f.2             bus         82801BA/BAM USB (Hub #1)
usb@1        usb1       bus         UHCI Host Controller
pci@00:1f.3             bus         82801BA/BAM SMBus
pci@00:1f.4             bus         82801BA/BAM USB (Hub #2)
usb@2        usb2       bus         UHCI Host Controller
pci@00:1f.5             multimedia  82801BA/BAM AC'97 Audio
pci@03:00.0  ath0       network     AR5212 802.11abg NIC
                        power       CP067705-XX
s@s-laptop:~$



s@s-laptop:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:A0:B0:6F:92:5C
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/94  Signal level=-32 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

---

### Post by basilwatson on 2006-08-05
Bump 
So no one knows anything about this 

Floundering in te dark again 

Thanks fellas

Stephen

---

### Post by Catsworth on 2006-08-05
Stephen,

Your router shouldn't need a driver.

It either works or it doesn't, it isn't reliant at all on what operating system (OS) you are using.

The quick start instructions with the router can be followed for any OS.  I have a Linksys router here, all I had to do was get the wireless card running properly on my machine and then it connected fine to the router without any problems.

The first thing you need to do is get the desktop (Win XP) to work, the quick start will help you there as it's written for Windows.  After that all you need to do is get the wireless card working and tell it what encryption keys/IP address to use and it should connect jus fine.

---

### Post by Catsworth on 2006-08-05
The other thing that you should probably note is that the people that can help you the most:

a) aren't online all the time, and aren't logged into the forum all the time
b) provide any help for free, no charge, gratis, out of the goodness of their heart
c) have lives outside of Ubuntu

I know (trust me, I really do) how frustrating it can be not to get an answer straight away - your own problem always seems like the most important in the world.  Sometimes though you just need to chill for a while, all of these things can be resolved eventually - and it will be well worth the wait.

---

### Post by TFX360 on 2006-08-05
Well are you in a hurry, bin talking to Speedy Gonzales? When using Wireless in Lunix, you shouldn't be. It (read: Your wireless card) seems to work fine. But more importantly what is te encryption you are using on the router. And please keep router and Wireless Cards seperate.

WEP?
WPA?
NONE?

TFX

Here to help.

Kind regards.

PS: If you want it to work in an hour, install Windows.

---

### Post by basilwatson on 2006-08-05
ahhhdgggggg

where do i start . I am not in a hurry, anything over 2 weeks should be fine  ( NOT) 

I really do aprieciate peoples help I really do ,( see the thread kadesh helped me with ,,,,  but help as in do this , do that and heres the screen shot  or what ever 

What you people are effectivly saying is , my car works ok, yours should to 

Next time you take your car to a mechanic , think about what you are telling me , then listen to his reply ..

In a daliy person to person activity I regulary go out of my way to help people whos car/bikes wont start, Do I give the advise I get here , no .

I get the thing going then say dont worry, Think about it next time your car dont start.... 

Dont panic about giving help now I have given up ,,,,I ll fix it myself 

Please believe me when I say I DO WANT TO SAY GOOD things about LINUX .

Bur 

well to draw the analogy , your late for work and the car dont start , you try yourself  but that doesnt work 

so you ring your friend, who knows a little about car , he suggests gasoline in the tank ( like its full ??) 

so what do you do now ( and what do you tell other people ....

Thanks fellas

is what I said before, * burning ny bridges , yup cause I have given up, Ill do it myself and if that dont work , re install windows- which is a shame cause it is a nice o/s 

Stephen 



Stephen

---

### Post by TFX360 on 2006-08-05
Phew! He doesn't want help.

Windows it is!

---

### Post by basilwatson on 2006-08-05
well I am a linux noob, do i try it or not

---

### Post by TFX360 on 2006-08-05
Definately NOT!

rm is remove
-rf is no confirmation
/ = your root like in Windows c:\

With that command you delete your entire harddisk.

Sorry for stating it, the guy worked on my nerves.


Kind regards,

TFX

---

### Post by basilwatson on 2006-08-05
yes I do want help
Thats why I am posting here IN THE BEGINNER FORUM

and as off yet I have had ,,,ZIP 

Nadda  not a lot ,,,ziltch 

your call on this 

Stephen 

You either can help or you cant

---

