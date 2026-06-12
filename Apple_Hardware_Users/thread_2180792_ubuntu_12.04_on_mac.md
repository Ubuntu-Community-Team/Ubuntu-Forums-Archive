---
title: "ubuntu 12.04 on mac"
date: 2013-10-14
forum: Apple Hardware Users
---

### Post by ClimateCrisis on 2013-10-14
hi,
i just bought an imac but i hate the mac OS ( please do not ask why i bought it :)), since i am a regular user of ubuntu, should i dual boot it or simply run linux with virtualbox.
if i run virtualbox i will miss the fast boot up tho :) but it is a small issue i can live with.
i have ubuntu the "old" 12.04 but not the ubuntu 12.04.3 ? version, does it matter if i just run my old 12.04 files, i suppose it will upload automatically to the new 12.04.3 ubuntu while it get installed ?


ps: i tought of just wiping out the entire disk and put linux on but for waranty issues i will wait :), anyway, mac OS is an easy fix for games and printer,etc. for now.

thx

---

### Post by mörgæs on 2013-10-15
> **ClimateCrisis said:**
> 
I have ubuntu the "old" 12.04 but not the ubuntu 12.04.3 ? version, does it matter if i just run my old 12.04 files, i suppose it will upload automatically to the new 12.04.3 ubuntu while it get installed ?



If you install an old 12.04 and update you will get to something close to 12.04.3. Don't worry that it's not an exact .3 , as it will be just as secure in use.

---

### Post by ClimateCrisis on 2013-10-16
ty morgaes.

well after trying virtualbox wiht linux has a guest , mac has the host.
too many bugs came up to my taste.

anyone knows a really tutorial , youtube vid or link, for a dual bool please.

i got imac 27 inch with mac OS mountain lion and want to put linux ubuntu on it .

ty

---

### Post by mörgæs on 2013-10-16
Moving the thread to the Apple tree. Maybe someone here can help you.

---

### Post by este.el.paz on 2013-11-01
> **ClimateCrisis said:**
> ty morgaes.

well after trying virtualbox wiht linux has a guest , mac has the host.
too many bugs came up to my taste.

anyone knows a really tutorial , youtube vid or link, for a dual bool please.

i got imac 27 inch with mac OS mountain lion and want to put linux ubuntu on it .

ty

CC:

Just stumbling through the list after posting on [PPC] . . . if you haven't found any answers yet . . . to dual boot on Intel you need a "boot manager" program . . . it ****used***** to be rEFIt, but that doesn't work for ML, so the upgrade is "rEFInd" . . . .  The guy who modified the first program into the second has a site that gives instruction for dual boot . . . just search "rodbooks" and see what shows up, or you can search the Sourceforge site with "rEFInd" . . . and then on the "support" page is a link to his instructions for how to install the program . . . .  I've just upgraded to ML and was trying to test out the CD . . . but it didn't work, so I don't recommend that way; he said to try the USB method . . . .  

It's not recommended to wipe the OSX from a Mac computer due to certain firmware issues, so dual boot is a better choice.  I'm trying to triple boot my MBPro, one for 10.6.8, another for ML or maybe Mav, and the last for Linux . . . .  OSX install wipes some stuff from Linux, so the Linux OS has to go in last . . . so I'm not in a rush and I haven't figured out if the rEFInd install is easy, problem free, or not . . . .  The other options, as you mentioned are to run Linux in Parallels, or VMFusionware, might be easier to do that, like the old Classic days; it's a little more fun to do the dual boot . . . .  

I don't recommend following rodbooks "Bootcamp" instructions though; I did that before and it seems BC "locks" the HD so that you can't modify the partitions size or number . . . .  I had to wipe the whole HD to change the partitions so I could in theory triple boot . . . but haven't done it yet.  I did have the dual boot 10.6.8 with Linux set up with rEFIt and BC . . . and it worked.

Good luck,

e.e.p.

---

### Post by davidchute26 on 2013-11-12
You can find everything you need to duel boot here - [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I agree with este.el.paz on the duel booting for firmware updates.

If you require any assistance with this - IRC: high_fiver on irc.freenode.org

---

### Post by este.el.paz on 2013-11-12
> **davidchute26 said:**
> You can find everything you need to duel boot here - [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I agree with este.el.paz on the duel booting for firmware updates.

If you require any assistance with this - IRC: high_fiver on irc.freenode.org

@David:

Thanks for your post, seems like the OP has moved on?  I took a brief look at your link, since I'm thinking about getting a dual/triple boot with two flavors of OSX and a Linux partiton on my MBPro . . . and it looks helpful, with caveat as I mentioned in my prior post, that rEFIt apparently doesn't work with Mountain Lion, whereas rEFInd is the updated version that is supposed to . . . .  Haven't had the time to get that going in my machine . . . the testing CD didn't seem to boot up in the Mac, so I'd have to try to test it on flash drive or just go for it and deal with the shakeout.  Point being the wiki suggests using rEFIt and the OP is running ML . . . I didn't check the link in that wiki for "iMacs newer than 11-1" . . . whatever that might be I don't have it.  : - )

e.e.p.

---

