---
title: "Macbook air question, recovery partition."
date: 2011-12-06
forum: Apple Hardware Users
---

### Post by willis on 2011-12-06
I'm thinking of getting a new 4.2(?) Macbook air and installing Ubuntu 11.10.  For the purpose of simplicity I'd like to single boot Ubuntu.  I read on the wiki that keeping OS X around is useful for firmware upgrades etc... so my question is: with the new Macbook Air's and their recovery partition, can't I just wipe the drive (except for the recovery partition) and install Ubuntu and then whenever I might need OS X for an upgrade, just recover back to it (I store all my work on dropbox, so a reinstall isn't bad).

I guess what I'm asking is after installing a single-boot efi install of Ubuntu can you still get to the Lion recovery with Command-R.  Or could I use the Lion recovery to create a USB drive as well?

Thanks!

---

### Post by jjex22 on 2011-12-06
Hi there! rEFIt detects the repair partition in Lion so you don't need command + R in my experience. That said, I'd say yes, if Apple don't give you an install DVD, you should create an install image from osx - either a DL dvd, or an 8GB usb stick and stick it in the cupboard - you've paid for the OS (Admittadly Lion is one of the cheapest OS's of all time - I paid less than £30 for my upgrade!) But it's yours, so why not make sure you have a copy incase you want to install it later, or your hard drive dies etc?

Unless you're really short on hard drive space, I'd keep OSX on there - it is a really good OS in my opinion, not much new for the average user in lion on SL or Leopard (I actually forgot that OSX changed until I booted into my Tiger based server!) But yes, if you don't need the space you can shrink a default install down to about 25GB (allows room for updates) and then just ignore it until you want it. If you need the space, then of course get rid of it - but make sure you've got an installation media handy!

---

### Post by willis on 2011-12-06
Great, thanks for your reply.  So just to verify, if I installed rEFIt, it would let me choose Ubuntu as the default os to boot?  I want the most seamless experience from "On" to the desktop...

EDIT: never mind, found what I was looking for: [http://hungrycoder.xenexbd.com/tutorial/setting-linux-as-default-in-refit-boot-loader.html](http://hungrycoder.xenexbd.com/tutorial/setting-linux-as-default-in-refit-boot-loader.html)

---

### Post by plumper on 2011-12-06
idk about the default on refit, as I've never tried to change that, but you could also install OS X to an external disk.  This would eliminate the necessity of employing partitioning.  You wouldn't have to waste your precious GB's on your puny solid state drive.  Simply pull out the external recovery disk when you need to perform a firmware update.  On the new Intel Macs you can boot off of USB drives without a hitch.  If you have another Intel-based Mac, you should be able to install Lion onto an external if you make a Lion boot CD (there are guides for this online) and install to a USB drive.  Also, another option would be to use a hub and perform the installation off of the MacBook Air, running off of an external optical drive.

This works on all of the Mac OS X installer disks I've tried (Tiger through Snow Leopard), however I have not given it a shot on Lion.  (I refuse to upgrade due to the lack of PowerPC compatibility.)

In my opinion, if you have the necessary boot disk and other items, this would be the simplest way to do it.  No fussing with which OS boots as the default etc., just straight Linux!!!

Tell me how it goes if you pick this route!

---

### Post by willis on 2011-12-06
Plumper, this is the route I was aiming for.  When are you given the option to make a recovery drive?  Is it inside OS X or in the bootloader?

I was envisioning with the new lion recovery partition just leaving that as is and using that as my "recovery drive" if the need should arise.  If I just straight installed ubuntu would there be a way to access that recovery partition before grub loaded?

---

### Post by markbl on 2011-12-08
Willis, FYI I recovered my new MBA recently from scratch. See [http://forums.whirlpool.net.au/forum-replies.cfm?t=1823995#r10](http://forums.whirlpool.net.au/forum-replies.cfm?t=1823995#r10).

---

