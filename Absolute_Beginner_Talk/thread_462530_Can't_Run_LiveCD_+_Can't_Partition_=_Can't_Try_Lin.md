---
title: "Can't Run LiveCD + Can't Partition = Can't Try Linux"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-06-02
Hi everyone,

I've been itching to try out linux for a while now and think that Ubuntu will probably be the best place to start. There are only a few problems:

I can't run ANY LiveCD on my laptop. I've tried a whole bunch of different distros including freespire, knoppix, ubuntu, etc. and all of them start the process but freeze midway through the startup process. With Ubuntu, I get the "respawning too fast" error that others have reported here in the forums. 

After these failures I decided that perhaps I should try creating a separate partition for Ubuntu. However, when I ran diskmgmt.msc in Vista Home Premium and attempt to "shrink volume," it says that 0 mb are available to create the second partition. 

My system is less than a year old. It runs Vista Home Premium (upgraded from XP Pro); has an AMD ML-34 (1.8 MHz) with 1 gig of ram. The graphics card is an ATI Mobility Radeon Xpress 200 series. My hard drive capacity is 75 GB with roughly 30 GB free. 

Any help would be much appreciated.

---

### Post by smoker on 2007-06-02
have you checked you cd drive, and have you got your bios setup to choose the cd rom as the 1st boot device?

if so many cd's don't work i would suspect the cd drive,

---

### Post by plinydogg on 2007-06-02
Smoker, thanks for your response and nice avatar! I haven't checked my bios setup because it seems clear that the boot order is correct because the LiveCD always starts to work (i.e., it clearly starts loading properly it just doesn't finish). But I understand what you're saying...if so many CDs don't work, it would seem that the problem must be in the CD player. But what could it be? 

If the boot order was not set up properly, the CD wouldn't be detected at all, right? 

Also, maybe I burned the CD improperly. All I did was burn the .iso image onto the CD. This is all I need on the CD right?

Thanks again for your help!

---

### Post by Lucifiel on 2007-06-02
Can we have your exact system specs? As in your laptop model?

Perhaps this could be an issue of "acpi". Are you able to get the "startup" screen? The one which comes with different options like "Run livecd" or "memtest", etc.?
If so, could you try pressing F6 at the startup screen and try this(without the quotes)?

> "linux acpi=off"

---

### Post by Lucifiel on 2007-06-02
Oops, I meant "try this code" as in "type it at the command prompt".

My apologies! :D

---

### Post by plinydogg on 2007-06-02
Lucifiel thanks for your response. I'll try your acpi suggestion and report back here in a few minutes. 

My model is an HP dv5216cl media center notebook (a budget model). Here are the specs:

umber   	EZ534UA#ABA
Microprocessor 	1.8GHz AMD Turion&#8482; 64 Mobile Processor ML-34
Microprocessor Cache 	1MB L2 Cache
Memory 	1024MB 333MHz DDR System Memory (2 Dimm)
Memory Max 	2048MB
Video Graphics 	ATI RADEON XPRESS 200M IGP
Video Memory 	128MB DDR (dedicated)
Hard Drive 	80GB 5400RPM
Multimedia Drive 	Super Multi 8X DVD±R/RW with Double Layer Support
Display 	15.4&#8221; WXGA High-Definition BrightView Widescreen (1280 x 800) Display
Fax/Modem 	High speed 56k modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 	54g&#8482; 802.11b/g WLAN with 125HSM / SpeedBooster support
Sound 	Altec Lansing
Keyboard 	101-key compatible

2 Quick Launch Buttons (HP Quick Play Music and DVD buttons)
Pointing Device 	Touch Pad with dedicated vertical Scroll Up/Down pad
PC Card Slots 	

    * 1 ExpressCard/54 Slot (also supports ExpressCard/34)
    * 1 Type I/II 32-bit card bus (also support 16-bit)

External Ports 	

    * 6-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Sticks, Memory Stick Pro, SmartMedia or xD Picture cards
    * 3 Universal Serial Bus (USB) 2.0
    * 1 Headphone out w/SPDIF Digital Audio
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 TV-Out (S-video)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 notebook expansion port 2
    * 1 IEEE 1394 Firewire (4-pin)
    * 1 Consumer IR

Dimensions 	10.4"(L) x 14.1"(W) x 1.38"(min H)/1.77"(max H)
Weight 	6.5 lbs
Security 	

    * Kensington® MicroSaver lock slot
    * Power-on password
    * Accepts 3rd party security lock devices

Power 	

    * 65W AC adapter
    * 6-Cell Lithium-Ion

What's In The Box 	HP Mobile Remote Control

Mobile Stereo Earbud Headphones (1 pair)

---

### Post by smoker on 2007-06-02
> **plinydogg said:**
> 
Also, maybe I burned the CD improperly. All I did was burn the .iso image onto the CD. This is all I need on the CD right?

hi, if you look at the cd in windows explorer, do you see the contents of the disk as one iso file, or a bunch of data files? if you see the disk as one iso, then you have burned it wrong and have to burn the iso as a data disk. there is info here if you need advice in this regard: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

if the disks are burned ok, have you another computer you can try them on? that way, if ok on another pc, you know your cd drive is faulty,

best of luck

---

### Post by plinydogg on 2007-06-02
Lucifiel and Smoker:

The acpi trick worked! I can't believe it! All that frustration gone in an instant. I can't thank you enough. 

Now, if you don't mind me asking, what is ACPI? I'm at least rudimentarily familiar with using a command prompt from the DOS 6.22 days but don't know what ACPI is. 

Thanks again!

---

### Post by smoker on 2007-06-02
glad you got it sorted, there's info about acpi here:  [http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)

glad Lucifiel was on hand with that tip, good to know:-)

---

### Post by plinydogg on 2007-06-02
Thanks for the link Smoker!

---

### Post by Lucifiel on 2007-06-02
Awesome!! :D 

Go get mad at Bill Gates for making ACPI not work on non-Windows operating systems. :p

---

