---
title: "boot powerpc iso from harddisc"
date: 2014-11-09
forum: Apple Hardware Users
---

### Post by greg63 on 2014-11-09
i would like to (leave macosx intact and) boot the lubuntu trusty live ISO from a PowerBook G4 harddisc.  how might i do this?

on a non-mac disc with grub already installed (if not already installed just use grub-install), it's easy to add (many) menuentries to boot (a collection of) ISOs.  the ISOs can just be downloaded into whatever partition/filesystem already exists.  no repartitioning, reformatting, nor mkfs necessary.  this works nicely on a hard disc or thumb drive.

i'm hoping it's (nearly) as easy on a ppcmac, but, is it?

i need to boot the ISO to run grub-install, but i need grub installed to boot it?

---

### Post by rican-linux on 2014-11-10
This blog has a great tutorial on installing Linux on PowerPC. He is using Debian but his section on partitioning the HD should be of help to you.

[http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-ii.html](http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-ii.html)

Also check out Ubuntu's [PowerPC FAQ ]("https://wiki.ubuntu.com/PowerPCFAQ") page, their [PowerPC Known Issues]("https://wiki.ubuntu.com/PowerPCKnownIssues") page, and their [PowerPC Installation Guide]("https://help.ubuntu.com/12.04/installation-guide/powerpc/index.html").

---

### Post by este.el.paz on 2014-11-12
> **greg63 said:**
> i would like to (leave macosx intact and) boot the lubuntu trusty live ISO from a PowerBook G4 harddisc.  how might i do this?

on a non-mac disc with grub already installed (if not already installed just use grub-install), it's easy to add (many) menuentries to boot (a collection of) ISOs.  the ISOs can just be downloaded into whatever partition/filesystem already exists.  no repartitioning, reformatting, nor mkfs necessary.  this works nicely on a hard disc or thumb drive.

i'm hoping it's (nearly) as easy on a ppcmac, but, is it?

i need to boot the ISO to run grub-install, but i need grub installed to boot it?

@greg63:

It's actually not clear what you are trying to do . . . boot a "live" iso?  Or you want to select various iso's to boot from, in which case you want something like "virtualbox" . . . an app that runs OS's, but "inside" OSX?  Or, Parallels, or VMFusionware . . . .

But, for the most part in PPC it isn't GRUB, it's Yaboot that is used to select from either booting into OSX or linux . . . .  But, right, dual boot is the general wisdom for running linux on apple hardware . . . .

e.e.p.

---

### Post by greg63 on 2014-11-14
> **este.el.paz said:**
> @greg63:
It's actually not clear what you are trying to do . . . boot a "live" iso?  Or you want to select various iso's to boot from, in which case you want something like "virtualbox" . . . 

But, for the most part in PPC it isn't GRUB, it's Yaboot that is used to select from either booting into OSX or linux . . . 
e.e.p.

yes boot (any of a collection of)(possibly live) iso's, don't need nor want virtualbox.  i'm hoping the iso's can simply be on the harddisc, grub2 and lubuntu can supposedly handle hfs+, though i wonder if the lubuntu live iso actually does include hfs+ capability.  booting iso's from harddisc or thumbdrive using grub2 is easy if not on a mac.

these 2 links
[http://glandium.org/blog/?p=2830](http://glandium.org/blog/?p=2830)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
describe booting without yaboot.  what advantage comes from using yaboot?

---

### Post by este.el.paz on 2014-11-15
> **greg63 said:**
> yes boot (any of a collection of)(possibly live) iso's, don't need nor want virtualbox.  i'm hoping the iso's can simply be on the harddisc, grub2 and lubuntu can supposedly handle hfs+, though i wonder if the lubuntu live iso actually does include hfs+ capability.  booting iso's from harddisc or thumbdrive using grub2 is easy if not on a mac.

these 2 links
[http://glandium.org/blog/?p=2830](http://glandium.org/blog/?p=2830)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
describe booting without yaboot.  what advantage comes from using yaboot?

@greg:

The short answer I believe is "no" . . . or, "I don't know" . . . .  Possibly with the intel apple computer it is possible that grub2 might be able to boot an iso . . . I'm less sure about doing that in PPC . . . in some ways it sounds interesting, rather than going through the install and cutting up the hard drive--I haven't seen anyone mention doing that before . . . except with VB.  For sure OSX doesn't "recognize" disks set up as linux . . . but possibly as I mentioned in another thread here, you might try SuperGrub2 CD and see if it will find and boot an iso . . . .

e.e.p.

---

### Post by rsavage on 2014-11-16
Booting the 'alternate' ISO with yaboot: [https://wiki.ubuntu.com/PowerPCFAQ#What_about_booting_the_iso_over_a_local_network_or_from_a_hard_disk.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_about_booting_the_iso_over_a_local_network_or_from_a_hard_disk.3F)

Using grub2 for a live/desktop ISO: [http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337)

Lubi using grub2 (the first stage of the instructions boots an ISO): [https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F](https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F)

---

### Post by rsavage on 2014-11-17
Forgot this too: [http://ubuntuforums.org/showthread.php?t=2225846](http://ubuntuforums.org/showthread.php?t=2225846)

---

### Post by este.el.paz on 2014-11-17
> **rsavage said:**
> Booting the 'alternate' ISO with yaboot: [https://wiki.ubuntu.com/PowerPCFAQ#What_about_booting_the_iso_over_a_local_network_or_from_a_hard_disk.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_about_booting_the_iso_over_a_local_network_or_from_a_hard_disk.3F)

Using grub2 for a live/desktop ISO: [http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337)

Lubi using grub2 (the first stage of the instructions boots an ISO): [https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F](https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F)

@r:

Thanks for that data, hopefully the OP will appreciate it . . . I guess this relates to the "wubi" thread you started some time back?  This somewhat goes to my post on the forum feedback sub-forum about the thinness of help on the apple forums . . . i.e., if you or str8bs were stopping by a bit more here I wouldn't have to waste my time posting bad intel . . . .  : - 0  But, if a post has been sitting unanswered for 7 or 8 hours here and I might know something, I try to reply . . . at least . . . .

But, still, interesting that there seems to be some info on the Lu user list that prior to some '06 time, apple units are not supposed to be bootable from USB drive???  And, same on the Yaboot being on the install rather than Grub2 . . . on PPC . . . why are using Yaboot if G2 can do more stuff ???  I will also take a look at jumpstarting iso's w/o install . . . whenever the next ppc iso come out . . . .

e.e.p.

---

### Post by rsavage on 2014-11-17
@eep, there should be no wasting of time, since the FAQ has ALL the answers (well for 12.04 at least which was the last version of Ubuntu and where my own support ends).  USB booting is covered well [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

---

### Post by este.el.paz on 2014-11-17
> **rsavage said:**
> @eep, there should be no wasting of time, since the FAQ has ALL the answers (well for 12.04 at least which was the last version of Ubuntu and where my own support ends).  USB booting is covered well [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

@r:

Agreed.  Probably most of the questions posted on the forum could probably be answered by the FAQ . . . ***if*** people were looking there . . . first or at all.  But, I have personally experienced some problems with google showing results for the FAQ . . . and I "knew" it existed . . . so, if they "don't know" it would probably be harder . . . .  And, then it seems some new issues have cropped up for PPC with 14.04 . . . .  

But, in the "stickies" at the top of the page, it doesn't say "PowerPCFAQ--for common issues . . . "  It says, "Where to download Ubuntu for PPC . . . and other frequently asked questions" . . . and then it's numbers of pages . . . .  For the beginner, that might not be too clear where to go . . . ????  I'm OK with my confusion, and if I had time I would read the FAQ cover to cover . . . .  Anyway, hopefully greg63 will find his answer in the FAQ . . . and maybe someday I'll look into the "wubi" thing . . . might be easier than doing the install each time a new iso shows up.

e.e.p.

---

### Post by rsavage on 2014-11-19
> **este.el.paz said:**
> then it seems some new issues have cropped up for PPC with 14.04 . . . .  


Not really.  I don't know why the lubuntu testing team felt the need to drop the 14.10 iso.  It had the same (radeon) problems as 12.10 and every subsequent release.  I proposed a solution way back then and got no support at the time.  The FAQ describes how the user can manually fix the problems with radeon, but implementing a solution would not be hard.

---

