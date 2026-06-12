---
title: "Problem installing"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by frazle on 2007-07-24
Hi,

I'm new to ubuntu & linux and having a bit of a problem installing it. Basically, I put the CD in & boot to the ubuntu installation and let it  do its thing, then I run the "Install" shortcut on the desktop and this is when the problem kicks in. It starts to load the installer window but the CD just keeps accessing without doing anything, and leaving it for 30mins doesnt make a difference, it just keeps reading the CD. I've checked the disc and it has no integrity issues.

My next plan was to install from a USB stick following the guide posted to the community help section, but when I run "syslinux -s F:" for the USB stick nothing appears to be written to the drive, so what am I doing wrong there?

Thanks for any help, cos i cant wait to get this working.

My spec: Intel centrino 1.6/256mb ram/ 64mb nvidia2go/40gb hdd

---

### Post by sad_iq on 2007-07-24
Could be a bad disk...have you md5 sum-checked it??? Have you burned the iso at the lowest speed(4x)???

---

### Post by RomeReactor on 2007-07-24
Hi. The problem could stem from the 256 MB you have in ram; on some systems, the graphical installer chokes because of that. I would suggest you download the [Alternate CD]("http://mirrors.xmission.com/ubuntu-cd/feisty/ubuntu-7.04-alternate-i386.iso"), which is not a live cd, and performs the installation in text mode only, but is (mostly) certain to work on your system.

I would also suggest you wait a while longer, in case someone else can offer you a better solution.

---

### Post by rhoderickj on 2007-07-24
> **frazle said:**
> Hi,

I'm new to ubuntu & linux and having a bit of a problem installing it. Basically, I put the CD in & boot to the ubuntu installation and let it  do its thing, then I run the "Install" shortcut on the desktop and this is when the problem kicks in. It starts to load the installer window but the CD just keeps accessing without doing anything, and leaving it for 30mins doesnt make a difference, it just keeps reading the CD. I've checked the disc and it has no integrity issues.

My next plan was to install from a USB stick following the guide posted to the community help section, but when I run "syslinux -s F:" for the USB stick nothing appears to be written to the drive, so what am I doing wrong there?

Thanks for any help, cos i cant wait to get this working.

My spec: Intel centrino 1.6/256mb ram/ 64mb nvidia2go/40gb hdd

The minimum to run the LiveCD is 256mb of RAM, so you're right at the threshold. I've personally seen 256mb systems do the exact same thing you've mentioned here. I won't even try a LiveCD install with less than 512mb of RAM because -- even if it works -- it's painfully slow. I recommend that you try the install with the alternate CD (which uses a text-based installer). It's not as pretty as the LiveCD but it's fairly easy to use.

---

### Post by frazle on 2007-07-24
Ok cheers, i'll try the alternate version. I'm trying to dual boot XP with ubuntu & am following a guide ( [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty) ) will I easily be able to spot & set all the parameters I need to in the alternate install?

Cheers.

---

### Post by rhoderickj on 2007-07-24
> **frazle said:**
> Ok cheers, i'll try the alternate version. I'm trying to dual boot XP with ubuntu & am following a guide ( [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty) ) will I easily be able to spot & set all the parameters I need to in the alternate install?

So you'll be doing a fresh install of both Windows and Ubuntu on a clean drive? It should be pretty straight-forward then. On the alternate CD, yu'll be given the same options as the LiveCD install, so you'll generally still be able to follow the guide you posted.

---

### Post by frazle on 2007-07-24
> **rhoderickj said:**
> So you'll be doing a fresh install of both Windows and Ubuntu on a clean drive? It should be pretty straight-forward then. On the alternate CD, yu'll be given the same options as the LiveCD install, so you'll generally still be able to follow the guide you posted.

Yep, I've done the XP install just got ubuntu to go.

Cheers for the help all, much appreciated.

---

### Post by RomeReactor on 2007-07-24
HermanZone offers a good guide to help you with text-mode dual-boot installation. When you load the page, just scroll down a few lines until you reach the option to **Choose one of three different Ubuntu 'Alternate CD' install guides** (see attached screenshot). If you installed XP in NTFS, the choose **Ubuntu+NTFS**.

---

### Post by dptxp on 2007-07-24
Download GParted. make a 2 GB (minimum 1 GB) SWAP partition at end of the drive (you can make anywhere).
You will be able to install from Live CD.
Your RAM is 256 MB. That is the problem.

---

### Post by hyper_ch on 2007-07-24
Alternate install disc isn't that difficult... the hardest part about it is, that you should READ what's written there ;) the second hardest part is the partitioner...
I would opt for manual partitioning there...
Just make sure, you have unpartitioned space and then use 512MB as a SWAP partition, about 5 GB as ROOT ("/") partition (ext3) bootable, and the rest as HOME ("/home") partition (ext3)...

---

### Post by frazle on 2007-07-24
> **RomeReactor said:**
> HermanZone offers a good guide to help you with text-mode dual-boot installation. When you load the page, just scroll down a few lines until you reach the option to **Choose one of three different Ubuntu 'Alternate CD' install guides** (see attached screenshot). If you installed XP in NTFS, the choose **Ubuntu+NTFS**.

What website do I find this on?

---

### Post by RomeReactor on 2007-07-24
Sorry about that! forgot to put [the link]("http://users.bigpond.net.au/hermanzone/").

---

### Post by frazle on 2007-07-24
> **RomeReactor said:**
> Sorry about that! forgot to put [the link]("http://users.bigpond.net.au/hermanzone/").

Cheers pal, lots to read there! I'll get cracking, I'm sure its less daunting than it looks... :D

Think its time I called samsung for some memory!

---

### Post by frazle on 2007-07-24
It seems to have hung on Installing the Base System @ 77%. I did a checksum of the ISO which compared perfectly against what it should be, and also checked the CD using the ubuntu boot menu, which said it was fine. Any ideas?

Might just switch off and try it again, see if it hangs at the same place, but seeing as the checksum was fine I can rule out the ISO being corrupt, correct? It just could be the CD?

EDIT: Got it working, just ran it again and it went through fine. Must say it looks very tasty :D

Time now to fiddle around!

---

