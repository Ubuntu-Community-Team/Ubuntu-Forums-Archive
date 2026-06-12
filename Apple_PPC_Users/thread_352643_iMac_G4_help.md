---
title: "iMac G4 help"
date: 2007-02-03
forum: Apple PPC Users
---

### Post by Clordio on 2007-02-03
Hello all,

I'm a total newb to the whole linux scene and I'm already running into problems. I've downloaded the edgy eft, dapper drake, and breezy badger(live cd) for ppc computers and even though I burn the iso to the cd (I've tried firestarter and mac's built in one) at slow speeds, and fast speeds it always burns fine(ie. all the folders are on there and everything) yet my mac refuses to recognize it as bootable. I go into the start up disc setting and my only options are network start up and mac os x start up. I've tried holding down c as I boot but nothing happens. I'm running 10.3.9, and really desperate for some help.

thanks,
Clordio

---

### Post by beanworks on 2007-02-04
Hmmm.  I've had problems using burned disks on older macs, but  hadn't tried it on a G4 iMac (I've got 10.4.8 running on it).  So  I burned a downloaded copy of 6.06 at 2x, using imageburner, and it wouldn't boot.  Then I tried a pressed disk, which works on the other macs when the burned disks don't, but that wouldn't boot either.  Tried different keys and combinations at the startup, but still got OSX instead.

I'm beginning to think it's the G4 iMacs, not Ubuntu.  It SEES the disk, just won't boot it.

Update: Oops - make that a G4 *eMac*

---

### Post by Clordio on 2007-02-04
Well those eMacs and iMacs of the 4G are pretty similar so I'd say you're on point. Is there maybe another distro I can use?

---

### Post by hellstead on 2007-02-15
hi there, i'm posting from an imac g4 1.25 running edgy.

if you do have an *Imac*, not an *emac*, i'm sure you're problem must be in the way you burnt your disc.

i used toast to make my installer disc, but if you don't have that,
follow these instructions: [http://www.macosxhints.com/article.php?story=20060619181010389]("http://www.macosxhints.com/article.php?story=20060619181010389")

it should work...

---

### Post by rccharles on 2007-02-15
> **Clordio said:**
> 
 I'm running 10.3.9, and really desperate for some help.

thanks,
Clordio

Here is how I burnt the ISO cd on my Mac with Mac OS 10.4 in the terminal:
hdiutil burn fileNameWhichEndsIn.iso

Do not know if hdiutil burn is in 10.3 or not.

Robert

---

### Post by grazie on 2007-02-15
If the md5sums and image burns verfy and you can see files and directories when you list the contents of the CD, you've probably burnt the CD image correctly. If you've done this, you could try reseting nvram and attempt booting from Open Firmware. Let us know what you've done and we'll detail a some more things. However, a few Macs do have hardware problems that make them difficcult to boot Linux.

---

### Post by Clordio on 2007-02-24
How do I reset nvram? And I've tried different boot keys other than c like the one for getting into open firmware, no dice. I'm using a wireless keyboard, is this a possible barrier? Is the signal of me pressing the key maybe not reaching the computer while it's booting? My iMac is an 800 mhz and I'm prettys sure it's architecture is different than the 1.25Ghz, they're different Revs. I've been looking at yellow dog lately, I'm not sure if it will work or not. Thanks for all your comments so far, please please more suggestions..:) 

Note: I have looked on other boards, and I've seen others with my hardware having the same problems but no one responding to them. It could possibly be the comp.

---

### Post by 3rdalbum on 2007-02-24
> **Clordio said:**
> How do I reset nvram? And I've tried different boot keys other than c like the one for getting into open firmware, no dice. I'm using a wireless keyboard, is this a possible barrier?

I would say that's probably the problem. If Command-Option-O-F does nothing at all, then the keypresses aren't being registered with Open Firmware. If you can borrow a wired keyboard, that would be a great help.

---

### Post by Clordio on 2007-02-25
Went out and got a wired keyboard from micro innovations (cheapo) still not registering key presses at boot. I'm about to break down and buy a mac specific keyboard.

---

### Post by rccharles on 2007-02-26
> **Clordio said:**
> Went out and got a wired keyboard from micro innovations (cheapo) still not registering key presses at boot. I'm about to break down and buy a mac specific keyboard.

Did you try the alt key ( options key on a mac keyboard ) when you powerup the machine?
This key will cause the mac firmware to display a list of bootable devices.

Robert

---

### Post by Clordio on 2007-03-02
> **rccharles said:**
> Did you try the alt key ( options key on a mac keyboard ) when you powerup the machine?
This key will cause the mac firmware to display a list of bootable devices.

Robert

Eureka! I finally got my hands on a new mac keyboard for cheap! 10 bucks plus shipping. Had the debian sarge ppc cd in the comp and held option and the linux cd is bootable! I'm gonna try ubuntu again, so I can try the live cd. Thanks to all those who helped. Is there an iTunes like   meda player for Ubuntu?

---

### Post by hellstead on 2007-03-16
> **Clordio said:**
> Eureka! I finally got my hands on a new mac keyboard for cheap! 10 bucks plus shipping. Had the debian sarge ppc cd in the comp and held option and the linux cd is bootable! I'm gonna try ubuntu again, so I can try the live cd. Thanks to all those who helped. Is there an iTunes like   meda player for Ubuntu?

wow, i'm surprised it was the keyboard...

as for itunes, i think [Amarok]("http://amarok.kde.org/") is a little less pretty, but a lot cooler.

---

