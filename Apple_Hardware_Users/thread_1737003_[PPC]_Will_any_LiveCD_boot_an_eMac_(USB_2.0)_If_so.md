---
title: "[PPC] Will any LiveCD boot an eMac (USB 2.0)? If so, which works best?"
date: 2011-04-22
forum: Apple Hardware Users
---

### Post by cfr42 on 2011-04-22
I administer (insofar as I am capable of doing such a thing) an eMac which is currently running OS X 10.3.9. This is becoming problematic because it is not compatible with current web browsers etc. It is also rather slow but this may just be the nature of the beast.

I would like to find a LiveCD for some version of Ubuntu or similar which can boot the machine and which I can have the machine's owner try out. So I don't want to use an alternate install CD, for example, because that would mean wiping the existing OS.

The eMac (USB 2.0) is, I believe, a PowerMac6,4 with a 1.25 GHz G4 processor 167 MHz bus 
It has a DVD/CD-RW Combo 40 GB disk
Graphics card: ATI Radeon 9200
ATI card model: ATY,RV280
Graphics connection: 4x AGP
Graphics memory: 32 MB 190 MHz DDR
17 " (16") 0.25mm dot-pitch CRT
Various resolutions from 640x480@120Hz to 1280x960@72Hz supported
Optional airport extreme card installed

I've been trying to boot using the PPC 10.04 LiveCD. I know the CD is correctly burnt. (The md5 sums given in the top directory check out and I can boot a powerbook with it aside from issues with the trackpad and, I suspect, non-optimal graphics support). I've tried the default "live" boot. I've also tried "live vga=791" and the fall back option for vga which I can't now remember but is given in the information before the yaboot prompt. The last of these works "best" in that I get to something which is clearly meant to be the desktop - the wallpaper shows up. However, nothing else appears. It is just the desktop background with no icons, menus or anything else. The other options I've tried do even worse. Either the splash hangs forever or I get an entirely black screen. Nothing I've tried is in any way usable and the only way to end seems to be to hold down the power button.

Is there any version of the LiveCD that will boot such an eMac and get a reasonably usable desktop environment? Since this is really just so the machine's owner can take a look, I'm not really bothered if the OS isn't up to date. I just need something usable and sufficiently Ubuntu-like to provide a feel for the OS.

Alternatively, is there any way to boot a PPC machine with Ubuntu installed on an external drive? Over firewire, say?

I don't know linux/ubuntu really at all so I'm somewhat at sea here and would like answers which take my ignorance into account! I hope I've provided sufficient information. Please let me know if not.

---

### Post by mondo2k on 2011-04-22
Hi! I'm more or less trying to do the same thing with a G3 iMac except I'm using the alternate ISO's and deleting Mac OS off the system.

To put it bluntly, you have a challenge ahead of you. Here's what you will need to do - [http://ubuntuforums.org/showthread.php?t=1146278](http://ubuntuforums.org/showthread.php?t=1146278)  The monitor issue makes the whole process very frustrating

At the very least you want to use Ubuntu 8.0.4 so it'll be a little easier for you to update the software. Xubuntu 6 is on my iMac and while it runs well, Firefox 2.0 stinks and I don't have enough current data libraries to install Opera, so I have to reinstall the whole mess again using Xubuntu 8.0.4 and hopefully update everything else online.

Also you may want to know that Firefox 3.6 is supposed to be the last version that is supposed to be ported to the powerpc platform. Not sure this makes any sense since today's video game consoles have ppc chips in them, but whatever...

Short answer: I don't think any LiveCD will "just work" in your eMac, but if you want to put some time in research and trial-and-error, you probably will get something to work.

---

### Post by oswaldkelso on 2011-04-23
I have a live Debian etch CD but you can't install from it and my tests would be of little use to you as my emac now has an LCD screen fitted. You would almost certainly  need to tweak your xorg from the terminal. You may find some clues in the old how to in my sig. YMMV

Another easy option if you have a spare fire wire drive is use carbon copy cloner on OSX. Clone OSX to the fire wire drive and do a proper install of Debian to the emac. If you want OSX back just boot from the firewire disk to clone it back. I say Debian as it's less buggy and once installed it will upgrade cleanly from each version to the next, and if the main user is not techie it will save you reinstalling every 6 months. Ubuntu does somethings very nicely but clean upgrades it not one of them.

The only real sticky point if you go the Debian route is if you need non free-firmware? It's an extra step.

clues on ccc here [http://forums.debian.net/viewtopic.php?t=18193#p96435](http://forums.debian.net/viewtopic.php?t=18193#p96435)

The good news is Debian will install and run. I have 4 G4's an emac 1GHz and an imac CRT. Just about all the issues on PPC are being addressed via the Debian PPC list (slowly).

Does the owner now there is no Adobe Flash? A blessing I assure you.

---

### Post by teachop on 2011-04-23
G4 eMac 1.25gHz is able to boot from the Live "CD" for 10.10 with no trouble.  It is too large to fit on a CD so burn it to DVD, hold down the "C" key, and it will boot.  Install from there, things mostly work.

Flash video options don't work properly.  That may be a show stopper.

I have Natty on this thing now, but used the alternate CD image.

---

### Post by cfr42 on 2011-04-23
Thanks. I will have to think about it I think. I just today tried installing Ubuntu on my own PowerBook and am having second thoughts about my own ability to cope with Linux.

Also, it turns out that the owner of the eMac does not seem to have quite followed my advice when originally buying the computer however many years ago. She complains how slow it is but has only given it 256MB of RAM. So there is really no question of getting a LiveCD to work with it independent of any other considerations. (I am annoyed with myself for not checking this before but I so clearly recalled discussing upgrading the RAM that it didn't occur to me it might only have a single original module.)

Firefox is a problem to be sure. Does anybody know what the plans are for firefox 4 in Ubuntu on PPC? There is a very nice version for OS X 10.4/5 on PPC. It isn't official and doesn't come in my preferred language but otherwise seems to believe it is FF 4 and behave accordingly. It has the added advantage of being optimised for different PPC processors - G3, two different versions of G4 and G5.

But no version of Firefox 3 or 4 will run in Panther so the eMac is still using Firefox 2.

---

### Post by teachop on 2011-04-24
> **cfr42 said:**
> Does anybody know what the plans are for firefox 4 in Ubuntu on PPC?
Firefox 4 is in Natty 11.04, and it works great.  However, flash is pretty important to browsing and the options are not really functional there, no fault of Firefox.

Having 256 megs sounds rough.  I have the same machine, but with 1Gig.

---

### Post by B_Free on 2011-04-25
[http://cdimage.ubuntu.com/ports/releases/8.04.1/release/](http://cdimage.ubuntu.com/ports/releases/8.04.1/release/)
This works. Update to 10.04 on line. It takes a long, long time to update. Ram is cheap.

---

