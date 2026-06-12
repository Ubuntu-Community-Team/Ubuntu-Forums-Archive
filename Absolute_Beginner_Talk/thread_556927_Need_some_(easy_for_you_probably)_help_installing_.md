---
title: "Need some (easy for you probably) help installing Wifi card"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by K7Avenger on 2007-09-21
I checked some other threads and I already saved you guys some time by typing in LSPCI

> lsjustin@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M



Now I found the XP drivers on Compaq's website.. now what do I do?  Please and thank you

---

### Post by overdrank on 2007-09-22
> **K7Avenger said:**
> I checked some other threads and I already saved you guys some time by typing in LSPCI



Now I found the XP drivers on Compaq's website.. now what do I do?  Please and thank you

00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Hi this link should help
[http://ubuntuforums.org/showthread.php?t=405990&highlight=00%3A09.0+Network+controller%3A+Broadcom+Corporation+BCM4306+802.11b%2Fg+Wireless+LAN+Controller+%28rev+02%29](http://ubuntuforums.org/showthread.php?t=405990&highlight=00%3A09.0+Network+controller%3A+Broadcom+Corporation+BCM4306+802.11b%2Fg+Wireless+LAN+Controller+%28rev+02%29)
Good luck!

---

### Post by K7Avenger on 2007-09-22
I downloaded the installer... and when I open the .py files it just opens a script.  I downloaded all the package updates too.
Wow... can't believe how hard this is when I thought Ubuntu was easy...  thanks for the help guys :(

I guess I need some python app?

---

### Post by K7Avenger on 2007-09-22
okay never mind, I just needed to exract it... my bad :mad:

Okay, I get to the point on the installer where it asks for me to put in the original install CD, so I do and hit enter like it says.  It then never says anything after that in the "null" prompt?

Help pleaseee :(

---

### Post by K7Avenger on 2007-09-22
Okay I quit the installer and retried, and got through the install process and rebooted.

The problem got worse.

Now all I see on the network select screen is "modem" and "wired", at least before the wireless card was listed?

Now what :(

---

### Post by anewguy on 2007-09-22
I'm going to point you to the how-to for my old laptop.  The very first section is about getting the broadcom 43xx series to work.  I think it should work for you and is pretty easy.  Let me know how it goes.:)

[http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215+how+to]("http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215+how+to")

---

### Post by Ramses on 2007-09-22
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

There is instruction how to use your windows driver for wireless.

---

### Post by anewguy on 2007-09-22
> **Ramses said:**
> [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

There is instruction how to use your windows driver for wireless.


I've always been curious, so I hope you don't mind if I ask - is compiling ndiswrapper really needed?  As shown in the above mentioned link to my old laptop how-to, I was able to get a Broadcom 4318 working just using the ndiswrapper and ndiswrapper-utils from synaptic package manager.  I have seen many mention recompiling ndiswrapper, and not being any kind of expert, I'm curious as to why it is needed.

Thanks!:)

---

### Post by K7Avenger on 2007-09-22
I am so confused right now and am at the point of just punching something :(  I have like 3 different faqs telling me to do different things.  The drivers I got are a simple exe file.  The installer the one guy linked me to removed the wireless icon from the network screend haven it was there before..

This is really upsetting.  The one faq is like six pages long of terminal commands, one requiring a URL to a driver I dont know for sure will work.

Oh my god... wow.  shouldd have just kept XP.  Someone please help me.

---

### Post by K7Avenger on 2007-09-22
Ramses, I did your walkthrough and got these errors partway through.  Just so you know, I copied and pasted most of the way through, no mistakes were made:

justin@ubuntu:~$ cd ~/bcm4306
bash: cd: /home/justin/bcm4306: Not a directory
justin@ubuntu:~$ cabextract sp33008.exe
sp33008.exe: No such file or directory

All done, errors in processing 1 file(s)
justin@ubuntu:~$ cabextract sp28537.exe
sp28537.exe: No such file or directory

All done, errors in processing 1 file(s)

---

### Post by K7Avenger on 2007-09-22
When the walkthrough told me to send the 4306 driver update to the folder, I did.  And when I try to use Cabextract to install it it says its not a directory, which it is.

This has to be the most frustrating computer experience ever.  Can someone point me to a definitive walkthrough, please?  please???

---

### Post by GSF1200S on 2007-09-22
> **K7Avenger said:**
> When the walkthrough told me to send the 4306 driver update to the folder, I did.  And when I try to use Cabextract to install it it says its not a directory, which it is.

This has to be the most frustrating computer experience ever.  Can someone point me to a definitive walkthrough, please?  please???

First off man... calm down :)  I know your pain.. my wireless card gave me HELL, but now it works with Feisty out of the box. Soon your card will be the same. 

Lets start simple: have you tried ndiswrapper? Just go into Synaptic and download it, along with the utils. I dont remember ndiswrapper 

Do you have the restricted drivers manager running? It should look like a circuit card in your system tray. Whats the NAME of your wireless card? LSPCI will list the chipset, but not the card name.. you may be able to use madwifi drivers as I do. Hit me back with these answers (please answer all of them) and Ill give it my all to get you in the net with your wireless card.

Diving into faqs blind can be hell.. you have to understand that Linux has SO MUCH hardware to write drivers for, its amazing were managing as well as we are.

---

### Post by K7Avenger on 2007-09-22
> **GSF1200S said:**
> First off man... calm down :)  I know your pain.. my wireless card gave me HELL, but now it works with Feisty out of the box. Soon your card will be the same. 

Lets start simple: have you tried ndiswrapper? Just go into Synaptic and download it, along with the utils. I dont remember ndiswrapper 

Do you have the restricted drivers manager running? It should look like a circuit card in your system tray. Whats the NAME of your wireless card? LSPCI will list the chipset, but not the card name.. you may be able to use madwifi drivers as I do. Hit me back with these answers (please answer all of them) and Ill give it my all to get you in the net with your wireless card.

Diving into faqs blind can be hell.. you have to understand that Linux has SO MUCH hardware to write drivers for, its amazing were managing as well as we have

I believe I have installed NDISWRAPPER.  but I'm not positive, and I don't know what synaptic is.

I don't know if the restricted drivers manager is running and I don't know where the system tray is on Ubuntu either :confused::confused:

The name of my wireless card I'm not sure of.  All I know is what was listed on the LSPCI thing.  Sorry.

Thank you for the help and walking me throughthis like the noob I am

---

### Post by Pumalite on 2007-09-22
[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

---

### Post by K7Avenger on 2007-09-22
> **overdrank said:**
> 00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Hi this link should help
[http://ubuntuforums.org/showthread.php?t=405990&highlight=00%3A09.0+Network+controller%3A+Broadcom+Corporation+BCM4306+802.11b%2Fg+Wireless+LAN+Controller+%28rev+02%29](http://ubuntuforums.org/showthread.php?t=405990&highlight=00%3A09.0+Network+controller%3A+Broadcom+Corporation+BCM4306+802.11b%2Fg+Wireless+LAN+Controller+%28rev+02%29)
Good luck!

I have great news guys!  After succesfully (after the 4th try, it kept freezing) using that threads program...

bricked my ******* laptop.

Now it won't even go 1/4th the way past the Ubuntu loading screen.  So I went from installing a wireless card to not even being able to get into the operating system.

Anyone that says Ubuntu is easy: :lolflag:

---

### Post by K7Avenger on 2007-09-22
Will someone please help me.  Please.  I'm seriously going crazy.  I cannot believe how frustrating this is.

---

### Post by K7Avenger on 2007-09-22
I tried booting in safe mode, all went well until it got to this point:

[  30.636000] ndiswrapper using IRQ10
[  30.976000] BUG! Soft lockup detected on CPU#0!

There were a a couple lines after but thats where the problem starts.  There should have been some sort of warning on that program that it could destroy Ubuntu... what now.. :(

I need this laptop for school guys.

---

### Post by Pumalite on 2007-09-22
What happened with this:


Code:

sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

from the terminal if you have a broadcom chipset

1. First, go into Synaptic Package Manager, and search for "ndiswrapper-utils"
NOTE: If you are running dapper or later i would recommend building ndiswrapper from source since i could not get this to work with the ubuntu provided ndiswrapper package. click here for instructions. thanks to trubblemaker for helping me solve this problem.

2. Install it. (DO NOT INSTALL THE PACKAGE FROM SYNAPTIC IF YOU BUILT NDISWRAPPER FROM SOURCE!!!)

3. Go into Terminal and go to the directory where the .inf file and .sys file(s) are for the driver. (I had the CD for mine, but if you don't have one, research how to find your driver.)

4. Type in "sudo ndiswrapper -i driver.inf", where "driver" is the name of the .inf file.
(example: My .inf file was called "netwg111.inf". Yours will probably be different (unless you have a Netgear WG111 usb or laptop card.)

5. Type in "sudo modprobe ndiswrapper"

6. Type in "sudo ndiswrapper -m"

7. Go into Networking (System > Administration > Networking

8. There should be a choice that says "Wireless Connection". It should also say that it is inactive.

9. Click "Wireless Connection" and then click properties.

10. Click "Enable this connection" and fill out the information accordingly. Make sure that you have the correct network name filled out. Type in the WEP key if your network requires one. My network is configured with DHCP, so I chose DHCP as mine. If your network is not configured with DHCP, select "Static IP Address" and fill out the information accordingly.

11. Internet should work at this point. If it doesn't, you probably don't have something configured right. Go back and check everything.

12. To make this enable itself every time you boot up, open a terminal and type in "sudo gedit /etc/modules".

13. Add "ndiswrapper" to the bottom of all the text. There! Wireless should be configured an ready to go!

14. (Optional) You should also install Wifi-Radar from synaptic to monitor and manage your wireless connection. Just go to Synaptic and search for wifi-radar.
__________________

---

### Post by K7Avenger on 2007-09-22
Puma, I can't do any of that because I used that guys program on the first page and now my computer won't even load into the operating system :|

---

### Post by GSF1200S on 2007-09-22
Dont give up man. Youre letting this fluster you, when its usually a very easy process. You have to understand that hardware support is better in Linux than anywhere else- its the fact that devs have to write them versus the hardware companies. 

No onto your problem. Now the damn thing wont reboot. Considering you were messing with network stuff, I would disable the network manager and go from there. 

I know.. how am I supposed to do that when the OS freezes?? When you first turn on the computer and Grub comes up, go to the option right below the one you usually use. This will not load any graphic Ubuntu stuff, and its a sort of troubleshooting boot. I had an Arch Linux kernel that would go into KERNEL PANIC (death in the linux world), and the second option would boot fine.

Once thats loaded and you login, type the following:

```
sudo nano /etc/default/NetworkManager
```

```
sudo nano /etc/default/NetworkManagerDispatcher
```

Then, type:

```
sudo reboot
```

Then, choose the selection you normally would at the grub screen. Im not sure on this, but im guessing you should be able to get to your desktop, because the network manager is disabled. Then, input the following command:

```
iwlist scanning
```

If you get a list of networks, than your wireless card **works,** its the network manager that doesnt. I had that problem, but id rather connect with the terminal anyway (network manager uses RAM and CPU, and the terminal seems faster to me).

Let me know how this goes.. Oh, and just so you know, getting angry will hurt you more than help you in any forums- I know it can be frustrating and it can be intimidating, but once the initial quirks are worked out, your prize will be waiting. :)

---

### Post by anewguy on 2007-09-23
Do you have much loaded to Linux, or are you just starting out?

If you are just starting out, PLEASE do yourself a big favor and reload Linux from the CD, then follow the link in my previous post.  It's not a matter of a url that MIGHT work.  If you want I can just post the 2 files needed here for you to download.  PLEASE, follow my instructions - it will take you 10 minutes tops, and it will work!  I've already had people with the 4306 use the instructions just fine.  The thing applies to the entire 43xx series.

---

