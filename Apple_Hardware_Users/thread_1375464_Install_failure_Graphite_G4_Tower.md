---
title: "Install failure: Graphite G4 Tower"
date: 2010-01-07
forum: Apple Hardware Users
---

### Post by CovenStine on 2010-01-07
I'm trying to install 9.10 on a G4, because osX 10.3 server won't recognize the 500Gig hdd my friend installed in it.
There's software you can buy to emulate the drive within 10.3, so I figure it's a software limitation.

Anyhow, no matter what I do (reset the P-Rom, hold C, hold alt, stand on my head) mr-fancypants-mac decides my boot CD isn't valid, and ejects it.
The default disk is too big for a CD, so I burnt it to DVD, that got ejected.
I downloaded the alternate via Bittorrent, that booted but the MD5 failed on one of the files at about 3% checked.  After that, the CD was always ejected without booting.
I re-downloaded the alternate via a mirror, checked it's MD5 before burning, and it matched the Bittorrent version.  I burnt it anyway, at 8x & verified the data (NERO), but it keeps getting ejected, too.
I'm quite befuddled.
Any suggestions?

Oh, and as far as other distros go, I'm JUST feeling like I'm not a complete Ubuntu noob, but I don't really have the patience to start over in a less noob-friendly -nix distro, so, I'd count that out, as far as my options.

---

### Post by linuxopjemac on 2010-01-08
try Debian Lenny PPC netinstall

---

### Post by CovenStine on 2010-01-08
...should I try reformatting the HDD or anything?  I really want to stick with Ubuntu, I don't have the ability to troubleshoot networking issues and hardware issues without a familiar starting point...

Would using Ubuntu even achieve what I'm trying to accomplish?
Is it possible to also use a non-Mac approved graphics card, so long as it's AGP?  I realize I'm kinda threadjacking myself.
Thanks lads

---

### Post by CovenStine on 2010-01-09
...would I have better luck with 7.10?
... I'd start working my way back, but I'm running out of CD's.  
sidenote: YellowDog's DVD didn't even register as non-bootable, the computer skipped right over it and went to OSX.
What is the bios looking for and not finding on these CD's?

---

### Post by oswaldkelso on 2010-01-10
Isnt there a size limit on that model of 137GB? anything over that wont be recognised. If you partition the drive so the first partition is less than that. It should work.

Google to confirm. :)

---

### Post by CovenStine on 2010-01-10
I wasn't sure if it was a hardware-level issue or not.
Think a non-mac HDD controller would work as an add-in card?  Or not, because it's x86 based?

I borrowed a friends' macbook and burned 9.04PPC w/ Disk Utility, still ejects the disk...
I'm going to try [this network install idea]("http://gn.iohazard.net/wiki/GN/UbuntuG4") next.


If that doesn't work, can I remove the hdd, put it in a x86 machine under 9.10, and somehow do a manual install of everything essential, so I can at least boot it & get on a network to get the rest?

---

### Post by CovenStine on 2010-01-11
So, no go on the netboot method, the patched Yaboot doesn't like 9.10.

However, I am wondering about using the text-based openFirmware.
I tried what I found on some mac forums "boot cd:, \\tbxi" , but \\tbxi isn't available on the CD.  I'm assuming that is a typical file found on your average mac OS cd, so... am I missing something?

---

### Post by linuxopjemac on 2010-01-12
tbxi is not a file....
[http://mac.linux.be/content/guide-open-firmware-apple-bios](http://mac.linux.be/content/guide-open-firmware-apple-bios)

---

### Post by B_Free on 2010-01-12
> **CovenStine said:**
> So, no go on the netboot method, the patched Yaboot doesn't like 9.10.

However, I am wondering about using the text-based openFirmware.
I tried what I found on some mac forums "boot cd:, \\tbxi" , but \\tbxi isn't available on the CD.  I'm assuming that is a typical file found on your average mac OS cd, so... am I missing something?

I'm not sure about the 500 gig HD, but since your iBook is a PPC try 
[http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/)
. Then upgrade from there. Only download the alternate CD because the Live CD doesn't have an install from the Live version. I had the same problem of having the CD eject from a Mac installed with a 10.4 installed. The computer with both 10.4 and Ubuntu 5.10 had no problem. The Ubuntu 9.10 still has the same downside of having to alter your screen size, sound, etc.

---

### Post by CovenStine on 2010-01-12
Hokay, so, I booted into both XP and Ubuntu, and neither o/s found anything with a filetype tbxi within the ISO's i have downloaded, and I did a cursory manual search of the 'alternate 9.10' cd, and didn't see any file that matches.
I dunno if they're straight up missing, or what, but somehow the 'alternate 9.10' disk booted once, so, I'm miffed as to why it was temperamental/picky, or worked at all.
Makes me think the only thing useful about this computer is the amazingly well engineered case...

---

### Post by lubod on 2010-01-13
Many (not all, but many) G4s have internal ATA controllers which cannot handle Hard Drives over 128Gb (no LBA support I think).

So 500Gb is a combined hardware/software limitation, but more a question of hardware than software, not limited to 10.3, happens in 10.4 and 10.5 too. It can be overcome with some software, but that is a work-around, not a permanent fix, and it means making special partitions so booting happens from those below 128Gb, and no partition cross this boundary, i.e. start below 128Gb and end above it. See more info here, it is about CUbes, but a Cube is one compact G4, and they discuss tower G4s as well:

[http://www.cubeowner.com/forums/index.php?showtopic=14157&pid=98143&mode=threaded&show=&st=&#entry98143](http://www.cubeowner.com/forums/index.php?showtopic=14157&pid=98143&mode=threaded&show=&st=&#entry98143)

And since it is partly software, it might break with a future software or OS update. Seems flaky to me, YMMV.

I'd recommend the hardware approach. If you want it internal, get a Mac compatible PCI ATA adapter, and go from there - no 128Gb limit. Maybe even go SATA and get the drive to match.

External in a Firewire/USB case - again no 128Gb limit. Firewire is better than USB for this, because there is no Firewire slower than 400Mb/s, and some faster, and you can boot all Macs that have it from whatever you attach that way. Macs that have itare all those from one of the early iMacs (second or third model, G3) to the current ones. Many G4 and older Macs have only USB1.x built in, and need a PCI card for USB2.x, and also booting from USB is more tricky. It is only somewhat supported on the really new Intel ones, and not at all on the older models, some people report having done it, but why take a chance when there is an alternate method that will work with less hassle.

On to the install CD - I'd suggest the mini CD for several reasons. Much smaller download, about 17Mb vs. 700. Can be burnt to a CD-RW, so if it fails, try again with an older/newer version, no coasters. Requires an internet connection during install (that's the downside, but if you can plug it into or connect wirelessly to a router or other computer with internet connection sharing, not a dealbreaker). It saves waiting for the 700mb download, only to discover upon first boot that Firefox and Open Office have updates made after the install CD was mastered, and you have 300 more mb to install after the CD!

URL for mini CD:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

you want PowerPC 32 bit (only G5 is b4 bit)

Maybe try burning at a slower speed, 1X, 2X, 4X whatever won't drive you batty with waiting. May make no difference, but it has been known to help sometimes, if only rarely.

As for why it won't boot the CD, is the CD drive in the Mac Apple supplied? Many non-Apple drives will not be bootable, that may be the only problem. If in an external case, is it USB or Firewire? USB will most likely fail, and even Firewire can be inconsistent, best to go internal if possible.

AGP cards: Early G4s (called Yikes, Gigabit Ethernet, etc.) have a 3.3V AGP 2X slot. Later ones (Digital Audio, Mirror Drive Door, etc.) have 1.5V 4X. 8X AGP may work in the latter ones but NOT in the early ones. Safest bet to get the lower AGP variety and work up from there. 3.3V AGP has two notches or gaps in the connector, not one. You may have to tape/cut pins 3 & 11 (those early Macs use them for Apple proprietary stuff, and AGP 8X for something else, so a generic PC card will not work electrically otherwise) and flash the firmware with a Mac specific one.

Refence:
[http://themacelite.wikidot.com/](http://themacelite.wikidot.com/)

The fact that booting from a 9.04 CD burned on a Mac failed suggest you no longer had the problem of the CD burning incorrectly in any way that matters, and that it could be the CD drive in the G4 is not bootable, either because it's non-Apple or because it's on a non-bootable port, etc.

Oh and the Karmic 9.10 mini CD linked above comes with yaboot in the iso and preconfigured, it has booted my G4 Cube successfully.
And it is a net install once the mini CD finishes loading.

HTH

P.S. The G4 has more to offer than a case :-)

---

### Post by CovenStine on 2010-01-13
So.
It worked, sort of.
I d/l-ed & burned the 9.10 iso, booted into it and launched the installer, no sweat.  It started giving me grief when it wanted me to pick a mirror to download from:
The only 2 options are 'manually specify' and 'united kingdom' for mirrors.
I have TFPD set up on my XP box, can I use that as a mirror?  None of the mirrors that I've looked at in the American Northeast have up-to-date PPC builds.
Suggestions?

---

### Post by CovenStine on 2010-01-14
Thanks very much for your help!
I do not understand why, but the minimal install CD booted fine, and the install went just fine through the UK server.
Much obliged.

---

