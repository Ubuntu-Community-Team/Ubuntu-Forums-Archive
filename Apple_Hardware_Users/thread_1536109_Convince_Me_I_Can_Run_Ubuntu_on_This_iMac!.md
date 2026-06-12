---
title: "Convince Me I Can Run Ubuntu on This iMac!"
date: 2010-07-21
forum: Apple Hardware Users
---

### Post by justcorbly on 2010-07-21
I've been an OS X user for about 5 years after using a variety of Linux distributions, including Ubuntu, for about ten years.  I switched to OS X because I got tired of chasing down drivers that were supposed to work but didn't.

I'm thinking about moving back to Linux.  But, first...

I've got an aluminum iMac, 20-inch screen, Radeon HD 2600 Pro, 2.66 GHz Core 2 Duo, 4 Gigs RAM, with the wireless aluminum keyboard and the wireless mouse.  I use a Time Capsule and a Brother HL 2170W printer in wireless mode.

How much of that hardware is going to work? By "work", I mean after the initial install or after pulling down some packages from an Ubuntu depository. I'm through with chasing around the net after fixes and drivers someone says worked for them.

I've looked around and found various ways people say they've been able to mount a Time Capsule drive. So, can I expect to be able to use my wireless Time Capsule as a backup drive with rsynch or something similar?

What about the sound?  I tried to use Ubuntu on a PPC Mac and sound never worked.

I'm not at all averse to tweaking a few scripts if needed.  But, I'm not at all interested in any kind of fix or driver that is not supported by Ubuntu or another major distribution.

---

### Post by kerry_s on 2010-07-21
sounds like you already know you should stay with os x.

come on it's apple hardware made to run apple software, it won't get any easier. :lolflag:

---

### Post by LtPitt on 2010-07-22
I quite agree with Kerry but remember that ubuntu today (in most of cases) simply works :)

try it to believe.

---

### Post by macewan on 2010-07-27
HP Officejet Pro 8500 works. Will test wireless mouse & mybook soon.

---

### Post by dementedgimp on 2010-07-27
I'm running an Imac, got it last January, and I just totally wiped out OSX in favor of Ubuntu 10.04, and it recognized my speakers, at least, and HP printer. I tried dual boot first, and it did not work.
yours,
Jacques P.

---

### Post by labaom on 2010-07-27
Ubuntu use to be a pain to install. Especially for those many PC computers. But Apple has its own section and there is an active community within Ubuntu that makes sure Apple + Ubuntu = works. PPC things can be screwy. But I know for a fact iMac Ubuntu will work. I have been using Tri boot for awhile with refit.

Want proof? There is a guide...

[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

I am more than willing to help you personally on AIM or something because I like converting people to Ubuntu. If you want help I can guarantee I can get it working 100%

---

### Post by justcorbly on 2010-07-27
OK, a Live CD boots fine. Apple's wireless mouse and keyboard don't work, but their USB cousins work just fine. I enabled wireless by "downloading" the BroadCom driver, which must be on the CD. That done, the Time Capsule and my Brother HL-2170W printer were found.  Couldn't print, though: The "Enabled" checkbox wouldn't retain my check.

I'm sure the printer will work after an install and the presence of a real drive on which to save config data.  Likewise, the wireless mouse and keyboard can likely be configured.

However, I was unable to generate any sound off the Live CD. I've seen several fixes for this, as well as a number of complaints that those fixes enabled sound, but without any bass, i.e., tinny audio.

So, sound is the last roadblock.  (It's an 8,1 iMac.)

BTW, it's been 3-4 years since I last dabbled in Ubuntu and Linux in general. THe software, and the site, look considerably slicker.

---

### Post by conundrumx on 2010-07-28
If you don't mind my asking, why switch?  You've got a lot of proprietary Apple gear, and I don't see your "quality of life" improving any with a switch.  Time Machine is in many ways superior to rsync as a means of backing up end user data.  I haven't tried the Bluetooth accessories, but somehow I doubt they'll be fully functional.

Obviously it's your computer, your time, your decision.  I'm just saying if you're ambivalent on OSX vs Linux...why change?

---

### Post by justcorbly on 2010-07-28
> **conundrumx said:**
> If you don't mind my asking, why switch?  You've got a lot of proprietary Apple gear, and I don't see your "quality of life" improving any with a switch.  Time Machine is in many ways superior to rsync as a means of backing up end user data.  I haven't tried the Bluetooth accessories, but somehow I doubt they'll be fully functional.

Obviously it's your computer, your time, your decision.  I'm just saying if you're ambivalent on OSX vs Linux...why change?

I'm not really ambivalent about it.  I think OS X, in terms of polish and style, is superior. I also make extensive use of apps like Yojimbo, DevonThink, and NetNewsWire.  As far as I know, no Yojimbo/Devon equivalents exist in Linux, and I haven't seen a Linux RSS reader that would convince me to drop NetNewsWire if it was an OS X app. 

But, like I said earlier, I spent close to 10 years with Linux before moving to Apple. At one point, I did try to install Linux on a G5, with mixed results.  So, this effort is driven by curiosity. 

I've actually just finished installing Ubuntu on the Intel iMac, retaining OS X in a shrunken partition. Sound, printing, and wireless are working appropriately. Sound required an incantation in the alsa config file and unmuting some channels. I wasn't able to enable my printer until I give it an "optional" name.  Creating a new partition with the Mac's Disk Utility was the biggest issue.  It spent an hour or so verifying and shrinking the drive only to throw an error, leaving the drive in need of repair.  I booted from the install disk and ran Disk Utility from the disk to do the repair. I also went ahead and successfully repartioned.

The Bluetooth keyboard and mouse are next. 

As I expected, Ubuntu feels a bit faster. That's subjective, of course, (I'm not gonna measure anything) but it counts.   I'll use it for at least a week or so before I make a  decision about keeping it on the drive.  If I can find acceptable alternative approaches to RSS reading and the  Yojimbo/Devon issue, and if I can tweak the display to my tastes, I  might stick with it.

---

### Post by conundrumx on 2010-07-28
I see.  I can't offer any alternatives to Yojimbo for Linux, unfortunately.

Most of my Linux needs were CLI, not GUI, so I just end up compiling the occasional odd utility for Mac and move on.

In the future, you might actually want to use the Boot Camp Assistant for dual boot setup.  Even though you're not using Windows, Linux still needs (prefers, really) BIOS emulation.  I recently went through a dual boot setup for kicks, here's how I did it:

Boot Camp Assistant to repartition.  When finished select Quit, not Reboot and Install.  Install rEFIt, reboot twice to verify functionality (rEFIt shouldn't show up after the first reboot).  Install Ubuntu, **make sure you put GRUB on the same partition as /, not the MBR.**  In order to do this I had to use parted to make the partitions by hand (one swap, one ext4), then select manual partitioning from the Ubuntu installer.  For some reason the installer wouldn't let me put GRUB on / when it was still technically a raw partition, even though it would be formatting it.  Reboot, and enjoy.

---

### Post by justcorbly on 2010-07-28
Well, I'll qualify my comment that Ubuntu seems pretty fast. Restoring hidden windows to the desktop takes 3-4 seconds.  Some of the apps I've played with today seem pretty slow.  The Liferea RSS reader is noticeably slower in operation than NetNewsWire.  For example, marking a stack of items as read takes a few seconds, while it is essentially instantaneous on NNW.

I have to say, too, that I'm a bit surprised that Gnome hasn't changed much since I last saw it.

---

### Post by P4man on 2010-07-29
About gnome; install compiz config settings manager and play around with that. if you like OS-X you should love those toys. Many are just eye candy but a lot are quite useful. 

But in general you're right gnome hasnt changed a whole lot, which I think is mostly a good thing. I just wish they finally made it usable for intelligent widescreen use (vertical panels, common guys its 2010!).

Last semi random thought: play around with gnome-shell. Its not finished yet but shows where gnome is heading. Im still not sure if im looking forward to it or not but its definitely... different. Very different :)

---

### Post by justcorbly on 2010-07-29
> **P4man said:**
> About gnome; install compiz config settings manager and play around with that. if you like OS-X you should love those toys. Many are just eye candy but a lot are quite useful.

I'm taking a look at it.  The first thing I did was to turn off all the wibbly, wobbly business when windows are moved.  Really annoying, at least to my tastes. With the ATI driver, window edges exhibit some unpleasant smearing along the edge opposite the direction of the move, even with all effects turned off. There's also some ugly screen flashing and distortion when the driver kicks in during startup and when it quits during shutdown.

I'm after sharpness and clarity of display, especially text.  Are there any packages I might install that improve on the default set up? (I recall in the "old days" hunting down TrueType fonts and hand editing X config files.)

---

### Post by P4man on 2010-07-29
Are you using the proprietary ATI driver or the OSS one?

---

### Post by justcorbly on 2010-07-29
> **P4man said:**
> Are you using the proprietary ATI driver or the OSS one?

I'm using the driver Ubuntu offered up to me when I ran "Hardware Drivers" after the install.  Didn't know there are two drivers.  What's the difference?

---

### Post by P4man on 2010-07-29
> **justcorbly said:**
> I'm using the driver Ubuntu offered up to me when I ran "Hardware Drivers" after the install.  Didn't know there are two drivers.  What's the difference?

the ones you have after a fresh install are the opensource drivers. What you got now is the proprietary closed source driver developed by ATI (and its probably the one you want).

---

### Post by justcorbly on 2010-07-29
Thanks.  I did notice that the driver identified the card as a "Mobility Radeon", whereas it's a "Radeon HD 2600 Pro".

---

### Post by justcorbly on 2010-07-31
Well, to wrap this up, I deleted the Ubuntu partition.  All the hardware was working, but the lack of, or a lack of quality, apps that I need turned the tide. Every RSS reader I tried was too slow. In particular, Liferea, which I think has the best design of Linux RSS readers I found, bogged down so much during subscription updates that it wouldn't respond to mouse clicks. 

Although I suppose I might have cobbled together something in an attempt to mimic their functionality, the lack of apps like Yojimbo or DevonThink, which I use throughout the day, was a compelling factor. I'd think this is an area for Linux developers. Don't Linux users also need to save, sort, search, tag, and recall mail, web pages, clips, PDF's, etc.?

On the hardware side, after I paired my Bluetooth devices on the Ubuntu side, they weren't recognized when I swtiched to the OS X side.  Then when I re-paired them in OS X, Ubuntu didn't recognize them.  Obviously, that's untenable.

---

