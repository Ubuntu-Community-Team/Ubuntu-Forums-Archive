---
title: "Cant boot sometimes, computer shutsdown."
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by SpoZen on 2007-04-25
Hi

Sometimes i cant boot up kubuntu, i tried booting in recovery mode then it says something about hardware error, and then it just shutsdown. Is there any way to fix this? Kinda lame to having booting up your computer 3 times before using it.

I wish i had some information about the error but the error text just displays for like 1 second.
I have manged to get this out: Network, ACPI and then something about a error. 

BTW is this called kernel panic?

---

### Post by xyz on 2007-04-25
If it is kernel panic, it would say so.
Can you jot down what error we're talking about here and post it.

---

### Post by SpoZen on 2007-04-25
> **xyz said:**
> If it is kernel panic, it would say so.
Can you jot down what error we're talking about here and post it.


I cant write it down because its just shown 1 second then my computer dies, but i could take a picture of it but then i gotta be hella fast, and my camera is so slow.

Print screen doesnt work either, only works using X rite?

---

### Post by xyz on 2007-04-25
Just a thought...
How about reinstalling from scratch...because if we don't know what error it is, it's kinda hard to know where to go from here!

---

### Post by SpoZen on 2007-04-25
> **xyz said:**
> Just a thought...
How about reinstalling from scratch...because if we don't know what error it is, it's kinda hard to know where to go from here!

Nah, i tried reinstalling, but when i boot the live cd i get the same error, thats why i installed with the alternative  CD.

But ill try to get a picture of the error tommorow. :)

---

### Post by pataphysician on 2007-04-25
wouldn't an error be written to /var/log/syslog or something along those lines?

---

### Post by kyphi on 2007-04-25
Your computer tells you that there is a hardware error that stops it from loading your programme.

The first thing I would do is to take the side off the machine and check that everything is seated properly:  graphics card, sound card, ethernet card, etc and especially the RAM modules.  These you may be better off to take out and reinsert until the retainers, top and bottom, snap into place.  Don't forget to unplug from mains power and also wear a wrist strap.

Good luck.

---

### Post by SpoZen on 2007-04-26
Okay i finally got some screens of the errors, but i had to record it thru a VHS using TV out and pause the tape and take photos of it with my camera. :lolflag: 

This is the last thing the output says: 
```
*Loading hardware drivers------------
NET: Registred protocol family 17
pci_hotplug Hot plug pci core version 0.5 
shpchp Sto Hot plug PCI controller driver version 0.4
Itco_vendor_support: vendor support:0 
itco_wdt (or w4t cant tell from the pic) Intel TCO watchdog timer driver version 0.4
itco_wdt found device .... 
itco_wdt intilazied heartbeat 30 sec
linux agppart interface v.0.102 
agppart detected an intel 830m chipset
``` 

Here is the best view at it: [http://img353.imageshack.us/img353/8898/00010br5.jpg](http://img353.imageshack.us/img353/8898/00010br5.jpg) (1,1MB) 
I can upload moore pictures if needed. 

kyphi, why should something be wrong about my computer? when XP works fine and i have been using edgy for like 3 months on it.

 
Heres my computer specs:

Hp omnibook 6100 laptop:
Im using 1ghz CPU, and 20GB harddisk.

General

    * Designation
    * Small business, Corporate business

    * System Type
    * Notebook

    * Built-in Devices
    * Display, Keyboard, Touchpad, Microphone, Pointing stick, Stereo speakers

    * Width
    * 12.8 in

    * Depth
    * 10.4 in

    * Height
    * 1.4 in

    * Weight
    * 6.2 lbs

    * Color
    * Black

    * Localization
    * English / United States

Processor

    * Processor
    * Intel Pentium III-M 1.13 GHz

    * Data bus speed
    * 133 MHz

Cache Memory

    * Type
    * L2 cache - Advanced Transfer Cache

    * Cache size
    * 512 KB

RAM

    * Installed Size
    * 256 MB ( 0 MB soldered) / 1 GB(max)

    * Technology
    * SDRAM - Non-ECC - 133 MHz

    * RAM form factor
    * SO DIMM 144-pin

Flash Memory

    * Type
    * None

Storage Controller

    * Storage controller type
    * IDE

Storage

    * Floppy Drive
    * 3.5" 1.44 MB floppy - Internal

    * Hard Drive
    * 30 GB

    * Storage Removable
    * None

Optical Storage

    * Type
    * 1 Internal

    * CD / DVD read speed
    * 8x

    * Compliant standards
    * CDi, CD-DA, CD-XA, Video CD, CD-Bridge, Kodak PhotoCD

Display

    * Display Type
    * 15 in TFT active matrix Integrated

    * Max Resolution
    * 1400 x 1050

    * Color support
    * 24-bit (16.7 million colors)

Video

    * Graphics Processor / Vendor
    * ATI Mobility Radeon - AGP 4x

    * Video Memory
    * DDR SDRAM - 16 MB

    * Analog video format
    * PAL, NTSC

Audio

    * Audio output type
    * Sound card

    * Audio output compliant standards
    * Sound Blaster 16/Pro

    * Audio Input
    * Microphone - Integrated

Input Device(s)

    * Input device type
    * Keyboard, Touchpad, Pointing stick

Telecom

    * Modem
    * Fax / modem - Mini PCI

    * Max transfer rate
    * 56 Kbps

    * Protocols & Specifications
    * X2 , Hayes AT command set, ITU V.90

Networking

    * Networking
    * Network adapter - PCI

    * Data link protocol
    * Ethernet, Fast Ethernet

    * Remote management protocol
    * DMI 2.0

    * Networking standards
    * IEEE 802.3, IEEE 802.3u

Expansion / Connectivity

    * Expansion Bays
    * None

    * Expansion Slots Total (Free)
    * 2 ( 1 ) x Memory - SO DIMM 144-pin, 1 ( 1 ) x CardBus - Type III (2 x type I / II)

    * Interfaces
    * 2 x USB - 4 pin USB Type A, 1 x Serial - RS-232C - 9 pin D-Sub (DB-9), 1 x Parallel - IEEE 1284 (EPP/ECP) - 25 pin D-Sub (DB-25), 1 x Infrared - IrDA, 1 x Keyboard / mouse - Generic - 6 pin mini-DIN (PS/2 style), 1 x Display / video - VGA - 15 pin HD D-Sub (HD-15), 1 x Display / video - S-video output - 4 pin mini-DIN, 1 x Headphones - Line-out - Mini-phone stereo 3.5 mm, 1 x Audio - Line-in - Mini-phone stereo 3.5 mm, 1 x Microphone - Input - Mini-phone mono 3.5 mm, 1 x Docking / port replicator - 240 pin docking, 1 x Modem - Phone line - RJ-11, 1 x Network - Ethernet 10Base-T/100Base-TX - RJ-45

Miscellaneous

    * Features
    * System password, Docking security, Power-on password, Hard drive password, Administrator password, Kensington MicroSaver security system

Power

    * Power device form factor
    * External

    * Voltage Required
    * AC 110/220 V ± 10% ( 50/60 Hz)

    * Power provided
    * 60 Watt

    * Compliant standards
    * EPA Energy Star

Battery

    * Technology
    * Lithium ion

    * Installed Qty
    * 1 / 2(max)

    * Mfr estimated battery life
    * 5 hour(s)

    * Recharge time
    * 2 hour(s)

Operating System / Software

    * OS Provided
    * Microsoft Windows 2000

    * Software type
    * HP TopTOOLS, HP DiagTools, McAfee VirusScan, InterVideo WinDVD, Adobe Acrobat Reader

Manufacturer Warranty

    * Service & support type
    * 3 years warranty

    * Service & Support Details
    * Limited warranty - Parts and labor - 3 years - Bring-in

---

### Post by Floor19 on 2007-04-26
I am having the same problem. 

Also no real error messages because the power cuts off but it happens when loading the modules (sound/external wireless card etc) drivers also the live cd stops at the same point.

In Edgy no problems at all so i do not think it is a hardware error.

Anyone any ideas otherwise it is back to Edgy.....

---

### Post by Cypher on 2007-04-26
What stands out to me there is that you have a watchdog timer running every 30 seconds. If noone "pets" the watchdog, it will trigger a hardware reset/halt.

---

### Post by SpoZen on 2007-04-26
> **Floor19 said:**
> I am having the same problem. 

Also no real error messages because the power cuts off but it happens when loading the modules (sound/external wireless card etc) drivers also the live cd stops at the same point.

In Edgy no problems at all so i do not think it is a hardware error.

Anyone any ideas otherwise it is back to Edgy.....

Is this random to you too? Because i can get in on my system sometimes.

Cypher, is it the watchdog who causes these problems?

---

### Post by Cypher on 2007-04-26
If it's behaving properly, then the watchdog driver is starting the timer and setting it's heartbeat interval to 30 seconds and as long as it can get the opportunity to run, things should be OK. If the watchdog timeout is triggering, it's behaving as expected, but it means that there is something running on the PC that is hogging up all the CPU power for more than 30 seconds..

---

### Post by SpoZen on 2007-04-26
So its CPU overload? Can i edit the timer so it doesnt shutdown my computer?

---

### Post by Cypher on 2007-04-26
Ideally, unless you're in a mission critical system, you generally don't want watchdog timers anyway. I would explore the option of completely turning it off..

---

### Post by Floor19 on 2007-04-27
Yes it is random and i am suspecting a kernel - network issue because when it does start i have to restart the network everytime.

But there are so many post about networking issues that i do not know were to start....

---

### Post by SpoZen on 2007-04-27
Is their any guides on how to shutdown the watchdog? 
Floor19, can you post your ouput before your computer dies?

---

### Post by Floor19 on 2007-04-27
I want to but i do not have the possibility. It does not give a error during boot it just shuts down. I also have problems with my wifi so i am back to edgy because that release rocks and i will merge to feisty over 3-4 months!

Cheers!

---

### Post by kyphi on 2007-04-28
To SpoZen

"kyphi, why should something be wrong about my computer? when XP works fine and i have been using edgy for like 3 months on it."

I run a dual boot system with XP and Ubuntu 6.06 on separate hard drives.  After collecting a new custombuilt computer from the makers 200 kilometers away I installed both operating systems but had intermittent problems with switching from one system to the other.  Often shutdown was incomplete and the machine had to be rebooted via the reset button.  Startup was also a haphazard affair, sometimes it would boot straight into the chosen operating system, sometimes a number of reboots would be necessary.  All very frustrating.  Once running, either operating system worked flawlessly.

It took quite some time and a lot of researching before I discovered that one of the RAM modules was badly seated.  Perhaps it worked loose during the journey home.  Since rectifying that I have been able to reboot successfully as well as shut down any of the operating systems.

Faulty functioning can not always be fixed by the command line.

Cheers
kyphi

---

### Post by SpoZen on 2007-04-28
> **kyphi said:**
> To SpoZen

"kyphi, why should something be wrong about my computer? when XP works fine and i have been using edgy for like 3 months on it."

I run a dual boot system with XP and Ubuntu 6.06 on separate hard drives.  After collecting a new custombuilt computer from the makers 200 kilometers away I installed both operating systems but had intermittent problems with switching from one system to the other.  Often shutdown was incomplete and the machine had to be rebooted via the reset button.  Startup was also a haphazard affair, sometimes it would boot straight into the chosen operating system, sometimes a number of reboots would be necessary.  All very frustrating.  Once running, either operating system worked flawlessly.

It took quite some time and a lot of researching before I discovered that one of the RAM modules was badly seated.  Perhaps it worked loose during the journey home.  Since rectifying that I have been able to reboot successfully as well as shut down any of the operating systems.

Faulty functioning can not always be fixed by the command line.

Cheers
kyphi

I see your point but the thing is i got a laptop, which is made to be portable. 
But ill check out the RAM modules anyway. 
Thanks

---

### Post by Joost Sikking on 2007-04-30
Hi all,

I got the same problem with my HP omnibook, so I don't suspect a hardware problem. Since the upgrade to Feisty, I have to reboot several times before the system gets to the login screen. With the previous dist, Edgy, I didn't have problems.
During startup the laptop just powers off, just before my PCMCIA wireless card is enabled. I read something about audio, it seems it happens just after the initialisation of it, I conclude that from the beeping of the boxes.
I tried changed the BIOS, booting without the PCMCIA-card, compiling a new kernel but none of it gave better results.
Please let me know how I can give more information to solve this issue.

regards,
Joost

---

### Post by Floor19 on 2007-05-02
Hi Joost,

I also have the problem on a HP Omnibook and also before the loading of PMCIA.

I can't give you advise regarding the solution but i should go back to Edgy (I did) or post a bug and try to get a solution from the develement guys...

There is already a bug. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892)

If there will be a solution a willl update but not before then!

No real help but who knows!

Groet,

Floris

---

### Post by SpoZen on 2007-05-03
It seems like many users have these thype of problems why can't somebody help, please?

---

### Post by mc00 on 2007-08-04
I know this thread is old, but I'm hoping there solution to this problem because I'm experience same problem as the rest of them..  so anyone know solution? I notice there is bug report in 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892)  nothing there yet. :(

---

### Post by Floor19 on 2007-08-08
Maybe you can try post [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)...

I did not try it so i cannot say it works but as it is a kernel issue maybe a newer kernel resolves it! (So it is on own risk as well ;)

If you tried can you tell me?

Good luck!

Floor

---

### Post by Joost Sikking on 2007-08-17
Hi all,

I tried the kernel 2.6.22-generic (manual procedure works fine) and after the first and second and third successfull I became enthousiastic.
But unfortunatly the fourth, fifth, sixth and seventh boot failed,
So my experience is that the new kernel didn't fix the Omnibook bug.

Regards Joost

---

### Post by Floor19 on 2007-08-21
> **Joost Sikking said:**
> Hi all,

I tried the kernel 2.6.22-generic (manual procedure works fine) and after the first and second and third successfull I became enthousiastic.
But unfortunatly the fourth, fifth, sixth and seventh boot failed,
So my experience is that the new kernel didn't fix the Omnibook bug.

Regards Joost

On [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89892) there is a workaround since yesterday. 

I am still happy with Edgy on my omnibook but if more people confirm the workarround maybe i give it another try!

Floor

---

### Post by pinguino13 on 2007-08-26
My computer would sometimes shut down at boot up and after trial and error it came to be the wrong setting in the BIOS  for my RAM.  My RAM  requires 2.1V to function at its full  potential. Not able to change voltage to RAM in BIOS I had to lower the speed of my RAM. Here are my specs:

GeForce6100SM-M Mother Board
Athlon 64 X2 6000+ processor
1 GB PC2 6400 OCZ RAM
Seagate SATA 300GB

---

### Post by Joost Sikking on 2007-08-26
Hi all,

The workaround works fine for me, I booted four times without a shutdown.

Just rename /lib/modules/2.6.22-9-generic/kernel/drivers/char/hw_random/intel-rng.ko or where ever intel-rng.ko is hanging out on your system (Find it by using locate intel-rng.ko),

Good luck,
Joost

---

### Post by mc00 on 2007-08-30
man I would love to try those workaround... but I can't even get passed "loading hardware drivers"  than powers off....  sometimes boots into the live cd just fine and even goes far partition my hard drive but power off afterwards when get to the part is going to prepare hard drive and install the stuff. I know for sure is not hardware relate because the laptop work fine with xp even vista(i was bored) and I have memory test/heat test/etc.. I have try 3 different distro I get the same sh!t power off and sometime I even manage to get it install but power off when try boot up into linux after the setup.. so like said I would love to try the workaround some people have posted.. Actually  linux is starting piss me off really bad, is going to leave bad taste for while.

for the heck of it, is there anyway to remove/rename  "intel-rng.ko"  in the cd or duirng boot option etc..?

---

