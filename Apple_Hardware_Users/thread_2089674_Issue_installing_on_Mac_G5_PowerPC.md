---
title: "Issue installing on Mac G5 PowerPC"
date: 2012-11-29
forum: Apple Hardware Users
---

### Post by vegasjon on 2012-11-29
Hello all!

I'm looking for some assistance installing on a Mac G5 PowerPC..I burned the ISO for Precise Pangolin  version. I have plenty of disk space and created a secondary partion on my primary drive. When I boot to the DVD to run the install I get the initial "Welcome to Ubuntu 12.04 LTS. After the "loading Ramdisk message, I get the white screen, then the next screen is a jumbled mess of color...I can hear the DVD spinning and thats it- no more messages. Any suggestions as to what I may have missed or am not doing?

---

### Post by mörgæs on 2012-12-03
Hi, welcome to the fora.

It's some old hardware. Ubuntu is probably out of the question, but Lubuntu is a good candidate. 

Remember to use the PowerPC ISO.

[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/)

---

### Post by keithmacleodlawder on 2013-01-21
I am an Ubuntu 'fresher' attempting my first install on a PowerMac G5 too.  I have spent several days on this, not wishing to let the machine win.  I've reviewed existing similar threads on this forum and taken the following steps:

- sourced my live CD from the PowerPC iso;
- attempted to install 12.04, but then decided not to proceed, following many failed attempts using various terminal commands recommended on this forum to amend video settings (the machine has a nvidia card) to move beyond the 'black screen of death', but still failed to get beyond a 'psychedelic' and very unstable graphical installer; then
- took forum advice to revert to 10.04 LTS (Lucid Lynx) (with a view to upgrading from it if successful) and have got to the end of an apparently perfectly functional graphical installer routine on 5 attempts, only to have the machine hang attempting to format new disk partitions for the installation.

The hang occurs when the installer has completed 5% of the format of the first new partition to Ext4.  Fans go into over-drive, the mouse locks and the only way out (after about an hour just to make really sure that nothing was happening) is a hard reboot and return to the beginning of the installation routine. 

I am using the auto installation option to reformat the entire target hard disk rather than partitioning manually.

I am attempting a dual OS installation (is this too ambitious?), leaving the original MacOS X 10.3.9 intact on the original 90GB Hard Drive A.  I have installed a new Western Digital 1GB Hard Drive B into the spare slot and this is the target drive for the Ubuntu installation.  This has been formatted to Mac OS Extended (Journaled) format using the OS X Disk Utility, which I have also used to verify it before commencing the Ubuntu 10.04 installation.

I am using ubuntu-10.04-desktop-powerpc.iso from  [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/) to burn my live CD.

I am using [https://help.ubuntu.com/10.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/10.04/installation-guide/powerpc/index.html) as well as this forum as my reference guide.

Many thanks for any help - because I'm beginning to run out of ideas!

---

### Post by mörgæs on 2013-01-22
Hi, welcome to the fora.

How does it work in a live boot?

---

### Post by keithmacleodlawder on 2013-01-22
Having had unsuccessful install attempts with Ubuntu 12.04 (Ubuntu and Lubuntu), I chose Ubuntu 10.04 from [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)  - where I am using the Mac (PowerPC) and IBM-PPC (POWER5) standard desktop CD.  I did this on the basis of commentary elsewhere in this forum which suggested it as a workround for G5 owners struggling with 12.04 in its various forms. 

I booted from the CD holding the 'c' key during restart and the installer seemed  to work fine.  It moved past all of the issues that had caused glitches before with 12.04 and continued until the part of the installation process where the target drive is partitioned.  I was using the automatic install - not attempting to re-partition the drive.  The installation screen shows a bar indicating progress in the format and partition process.  It stopped at 5%, the mouse stopped moving and the fans kicked in on overdrive.  I've run the routine twice now and exactly the same error happens both times.

---

### Post by rsavage on 2013-01-23
It's probably how you've formatted your drive (journalled) and hopefully it is bigger than 1GB. The recommendation to install 10.04 now is not very good. It only has a few months left of support and the upgrade process on PowerPC is untested. You can easily get 12.04 running - just read the PowerPC FAQ and Known Issues pages rather than spending your time searching forums.

---

### Post by mörgæs on 2013-01-23
Let's forget hard drive and installation for a moment. Again, how does it work in a live boot?

---

