---
title: "HP Pavilion dv9207us (dv9500) Entertainment Edition Notebook"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by elgormando on 2007-09-09
I was wondering if anyone had tried 7.04 (Feisty Fawn) on a HP Pavilion dv9207us (dv9500 series according to HP) Entertainment Edition Notebook.  If I can't get this to work, I have to go back to the Windows Vista that came with it (for crying out loud, please somebody help!!) because I need this laptop.  I'm fairly new to ubuntu, I've fooled around with it and have successfully installed it a couple of places, but would really start to use it and move as far away from Windows as possible.  I'd like to put together as many notes as possible for this model and keep them in one place for anyone else trying to do this, should I start a separate thread and link it here?  Here's the specs for the laptop:

**Microprocessor** - 1.73 GHz Intel® Centrino® Duo mobile technology featuring Intel® Core &#8482; Duo processor T2250
**Microprocessor Cache** - 2MB L2 Cache
**Memory** - 1024MB DDR2 System Memory (2 Dimm)
**Video Graphics** - NVIDIA GeForce Go 7600
**Video Memory** - up to 256MB (discrete)
**Hard Drive** - 120GB (5400RPM) Hard Drive (SATA)
**Multimedia Drive** - LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
**Display** - 17.0" WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
**Fax/Modem** - High speed 56k modem
**Network Card** - Integrated 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector)
**Wireless Connectivity** - Intel® PRO/Wireless 3945ABG Network Connection 
**Sound** - Altec Lansing
**Keyboard** - Notebook keyboard with scroll bar and integrated numeric keypad
**Pointing Device** - Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad (I have an external that works great for this, so this is as big of a problem if it doesn't work)
**PC Card Slots**
&#8226;	1 ExpressCard/54 Slot (also supports ExpressCard/34) External Ports
&#8226;	5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards 
&#8226;	4 Universal Serial Bus (USB) 2.0
&#8226;	1 Headphone out w/SPDIF Digital Audio
&#8226;	1 microphone-in
&#8226;	1 HDMI
&#8226;	1 VGA (15-pin)
&#8226;	1 TV-Out (S-video)
&#8226;	1 RJ-11 (modem)
&#8226;	1 RJ -45 (LAN)
&#8226;	1 Expansion Port 3
&#8226;	1 IEEE 1394 Firewire (4-pin)
&#8226;	1 Consumer IR

Also comes with the HP ExpressCard Analog TV Tuner/PVR with Remote Control (I'd like to get this working as well)

If at all possible I'd like to keep the Vista that came preloaded simply because there are a few apps that I still need to use that are Microsoft based and there's no Linux version or comparable Linux app yet.  Not a major requirement if the Linux works great!  I saw that someone from the Argentina team has some posts about kubuntu on the same model, but it's all in Spanish and I don't know a lick of Spanish.

Thanks for the help in advance!

---

### Post by overdrank on 2007-09-09
Hi and thanks for all the info but you do not state if you have tried to install or use the live cd. This link may help you to install along side vista. 
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by Brightbelt on 2007-09-09
Hi,
I ran Ubuntu on an HP dv9030us laptop really well, although I can't say anything about the built-in webcam. Some said it worked out of the box with some simple configuration, while others had some difficulties there. I never approached trying to use it. 

To check out your video card with Ubuntu, see this: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) 

It is worth knowing as much as you can about your video support ahead of time. And like the other fellow said, run the live CD. That's always a good start.

For what it's worth, on my DV9030us, the wireless worked right out of the box - I barely ever had to touch it. 

Also Google, the "HP DV9000 Thread" and it may help you see what's been done. It was that thread that gave me the confidence to install Ubuntu on my HP laptop in the first place.

Good Luck !
Frank B.

---

### Post by Brightbelt on 2007-09-09
Also see this [https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard) 

It's a more community-based support page but there may be some relevant info. 

Also, I'm aware that your HP 9207 may be in a totally different class than the DV9000s, but I'm sharing in case there may be some 9000-type of continuity there. 

Thanks, Frank B.

---

### Post by Brightbelt on 2007-09-09
Even better - [https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9297ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9297ea) ;)

---

### Post by elgormando on 2007-09-16
Thanks for the links, they were very helpful.  I'm in the middle of loading and configuring a fresh install of Feisty Fawn Desktop on this system right now, and vigorously writing down everything that I do.  So far, no issues at all.  I'll post what happens, thanks again!

---

### Post by elgormando on 2007-09-17
First, I loaded Feisty Fawn 7.04 Desktop (downloaded from ubuntu site) on my HP Pavilion dv9207us (dv9500 series according to HP) Entertainment Edition Notebook; once I was connected to the internet I ran the Update Manager to get any upgrades to the default installed applications.  So far, there are no issues with the system hanging or doing anything strange, but we'll see if this changes once I start loading applications on the system.

Here's another quick rundown on the system specifications from HP's website.  If you are using an HP to load this on, you may want to be sure you know exactly what your system is.  I only mention this because I wasn't sure whether to load the 32 or 64-bit version on my system because I didn't know exactly what the number was and what it was capable of (you'd think that they would provide this in the box, no such luck).  After researching the processor, I found mine was 32-bit.  If you find yours is 64-bit, you might want to search around, because I've seen a couple of threads saying that the 64-bit version on HP laptops really works nicely.  To find your system model number, lift up your laptop and look on the bottom.

System Specifications:

**Microprocessor **- 1.73 GHz Intel® Centrino® Duo mobile technology featuring Intel® Core ™ Duo processor T2250
**Microprocessor Cache** - 2MB L2 Cache
**Memory** - 1024MB DDR2 System Memory (2 Dimm)
**Video Graphics** - NVIDIA GeForce Go 7600
**Video Memory** - up to 256MB (discrete)
**Hard Drive** - 120GB (5400RPM) Hard Drive (SATA)
**Multimedia Drive** - LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
**Display** - 17.0" WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
**Fax/Modem** - High speed 56k modem
**Network Card** - Integrated 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector)
**Wireless Connectivity** - Intel® PRO/Wireless 3945ABG Network Connection
**Sound** - Altec Lansing
**Keyboard** - Notebook keyboard with scroll bar and integrated numeric keypad
**Pointing Device** - Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad (I have an external that works great for this, so this is as big of a problem if it doesn't work)
**PC Card Slots**
• 1 ExpressCard/54 Slot (also supports ExpressCard/34) External Ports
• 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
• 4 Universal Serial Bus (USB) 2.0
• 1 Headphone out w/SPDIF Digital Audio
• 1 microphone-in
• 1 HDMI
• 1 VGA (15-pin)
• 1 TV-Out (S-video)
• 1 RJ-11 (modem)
• 1 RJ -45 (LAN)
• 1 Expansion Port 3
• 1 IEEE 1394 Firewire (4-pin)
• 1 Consumer IR
• HP ExpressCard Analog TV Tuner/PVR with Remote Control (external card)

Here's a rundown of what I have seen and worked so far:

**[COLOR="Navy"]> Video device (NVIDIA GeForce Go 7600)[/COLOR]** - Icon popped up on the toolbar to enable the restricted driver for this device.  I enabled here, but also saw that this driver was available in the repositories as well.  It automatically downloaded the drivers for this and after restarting, the graphics have a definite improvement.  I don't do much with 3D or games, but is was definitely worth it because the graphics are sharp.

[COLOR="Navy"]**> Network devices**[/COLOR]
**Fax/Modem** - High speed 56k modem - *Still need to test this device.*
**Network Card** - Integrated 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector) - Worked from the fresh install with no further configurations needed.
**Wireless Connectivity** - Intel® PRO/Wireless 3945ABG Network Connection - Worked from the fresh install; I connected to my network running 128 bit WEP in about twenty seconds.  I plan on trying other authentications, just to ensure that there are no issues.

**[COLOR="Navy"]> Keyboard and Touchpad[/COLOR]** - Both work from the fresh install with no issues.  I actually use a Logitech Optical Wireless USB mouse, which also worked with no further installations required.
[COLOR="Navy"][B]
> Power[/B][/COLOR] - No problems with the battery as of yet.  I plan on purging the battery, as HP recommends, in the next couple of weeks.  The power monitor works as well.
[B][COLOR="Navy"]
> QuickPlay Launchbar [/COLOR][/B]- This laptop has a pushbutton bar at the top of the keyboard used for HP's QuickLaunch software.  I haven't tested with any of the media applications, but the volume and mute buttons on this both work.

More to follow over the coming weeks.

---

### Post by des4ij on 2007-09-25
Hey i have the same exact laptop... Ubuntu Studio (Feisty) works awesome and so does compiz fusion... but I cannot seem to get the webcam to work :-/...

---

