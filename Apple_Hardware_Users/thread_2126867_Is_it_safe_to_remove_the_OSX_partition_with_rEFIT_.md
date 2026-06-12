---
title: "Is it safe to remove the OSX partition with rEFIT installed?"
date: 2013-03-18
forum: Apple Hardware Users
---

### Post by Future Warthog on 2013-03-18
Is it safe to do this/will GRUB take over, or is there something I would need to do to make it safe?

---

### Post by este.el.paz on 2013-03-19
> **packpatfan said:**
> Is it safe to do this/will GRUB take over, or is there something I would need to do to make it safe?

@ppf:

I believe I asked this or a similar question awhile back . . . rEFIt is installed in or in front of the OSX partition, and it's main purpose is to synchronize multiple partition systems, like if you want to dual or perhaps triple boot.  Once it does that there is no need for rEFIt.  If you aren't going to dual boot with OSX then you don't need rEFIt and you don't need GRUB for that matter??  Not sure if you need GRUB to boot a single system, it might just go to the splash window and then the log in.  But, is anything "safe"???  If you have your system cloned on an extHD you could test out your plan there first--you can always reinstall everything if it isn't what you like.  Point being if you erase the OSX partition, probably rEFIt will also be erased, or you could erase it while erasing OSX.  Personally I like a dual boot system, because it gives me options.

e.e.p.

---

### Post by rmorr on 2013-03-22
It's been said elsewhere but the caveat is this: without an OS X install you won't be able to get firmware updates.

---

### Post by este.el.paz on 2013-03-22
> **rmorr said:**
> It's been said elsewhere but the caveat is this: without an OS X install you won't be able to get firmware updates.

@rmorr:

This is a good point, discretion is the better part of valor . . . might be why I kept my dual boot set up on all my Macs.  But, question is, is Apple actually doing firmware updates anymore?  It's literally been years since I've had any firmware updates on the machines that I have, an iMac since '00, an iBook since '04, and a MBPro since '10 . . . haven't seen one since the iMac waaaaaay back when.  Don't know if I just got lucky or it could be that the apple product is so refined they don't need it??  And it seems they expect folks to be buying a new one every couple years . . . or go into their iLease program . . . so they get a new computer at 3 or maybe 5 years for a flat rate each month.  With the price of them now leasing is going to become the only way working folk could get their grimey hands on one . . . .  : - )))

Anyway, your answer is the better answer, it's good to keep a partition with OSX on an Apple computer, not only does it seem to run the computer and graphics very well, but some maintenance stuff might need to be done thru it, etc.  The thread question is a tad flawed, it might better to ask if it's safe to remove the rEFIt partition with OSX installed.  But could firmware updates be done through the specific manufacturer of the item that would be affected?  Like the motherboard could be updated thru the motherboard maker . . . if need be?  No?

e.e.p.

---

### Post by rmorr on 2013-03-22
> **este.el.paz said:**
> @rmorr:

This is a good point, discretion is the better part of valor . . . might be why I kept my dual boot set up on all my Macs.  But, question is, is Apple actually doing firmware updates anymore?  It's literally been years since I've had any firmware updates on the machines that I have, an iMac since '00, an iBook since '04, and a MBPro since '10 . . . haven't seen one since the iMac waaaaaay back when.  Don't know if I just got lucky or it could be that the apple product is so refined they don't need it??  And it seems they expect folks to be buying a new one every couple years . . . or go into their iLease program . . . so they get a new computer at 3 or maybe 5 years for a flat rate each month.  With the price of them now leasing is going to become the only way working folk could get their grimey hands on one . . . .  : - )))

Anyway, your answer is the better answer, it's good to keep a partition with OSX on an Apple computer, not only does it seem to run the computer and graphics very well, but some maintenance stuff might need to be done thru it, etc.  The thread question is a tad flawed, it might better to ask if it's safe to remove the rEFIt partition with OSX installed.  But could firmware updates be done through the specific manufacturer of the item that would be affected?  Like the motherboard could be updated thru the motherboard maker . . . if need be?  No?

e.e.p.


This may not be the ideal answer (I'm still learning) but the EFI partition is what Apple uses to pass firmware updates (if you installed rEFInd to the EFI partition and not your OS X partition the Apple directory there is where that magic happens) ... so I don't think you can safely remove that partition without negating the possibility of firmware updates. You also still may want it if you EFI boot Ubuntu... but I also don't think you can easily set your target disk to a Linux install because OS X can't natively read ext partitions like you can with a Bootcamp Windows install which means you might need to get a little creative.

If you are EFI booting Ubuntu (I recommend this) you should have a GPT map, so resizing your partitions ought to be less of a challenge. I'd try resizing the partitions so that OS X takes up minimal space (Ideally, I'd do a clean install -- I usually do when I change things) and then I'd edit the rEFIt/rEFInd configuration file to make Ubuntu default and lower the delay time to a second. Not as fast, of course, as booting directly into Ubuntu but it would minimize time in the boot loader but still leave me the option to use OS X for any firmware, hardware stuff that I couldn't do with Ubuntu.

---

### Post by este.el.paz on 2013-03-23
> **rmorr said:**
> . You also still may want it if you EFI boot Ubuntu... but I also don't think you can easily set your target disk to a Linux install because OS X can't natively read ext partitions like you can with a Bootcamp Windows install which means you might need to get a little creative.

If you are EFI booting Ubuntu (I recommend this) you should have a GPT map, so resizing your partitions ought to be less of a challenge. I'd try resizing the partitions so that OS X takes up minimal space (Ideally, I'd do a clean install -- I usually do when I change things) and then I'd edit the rEFIt/rEFInd configuration file to make Ubuntu default and lower the delay time to a second. Not as fast, of course, as booting directly into Ubuntu but it would minimize time in the boot loader but still leave me the option to use OS X for any firmware, hardware stuff that I couldn't do with Ubuntu.

@rmorr:

I don't think we are disagreeing on the issue of whether keeping OSX is a good idea, and I'm not a technical CLI user of Linux, but my understanding is that intel Macs all are "EFI booted" and that Windows are BIOS? . . . and possibly Linux can go, uh, both ways.  So anything on Intel Mac would be booted EFI; question is whether an app like rEFIt is needed to boot Linux as a single system on a Mac, or whether GRUB would even be needed.  All these questions are irrespective of whether firmware updates could be done w/o OSX.

In terms of needing a clean install on OSX, in PPC yes, the only way to re-format the disk is to erase the whole thing and re-install each system, and then Yaboot is the boot loader, no rEFIt needed; in Intel Mac, I can say from personal experience that it isn't necessary to wipe OSX, but if it is then it should be installed first, then the rEFIt, then the other systems, but like I said I haven't found it possible to make changes to the Bootcamp partition set up once it's made, so possibly you could get 3 partitions set up from the get-go, but not once you've cut it to two . . . .  Hence my advice to find another way other than Bootcamp. Your experience may be different, etc.

e.e.p.

---

### Post by crjackson on 2013-03-23
> **este.el.paz said:**
> @rmorr:

question is whether an app like rEFIt is needed to boot Linux as a single system on a Mac

This is exactly my question too.  I just got a new (my first) Mac Pro listed in my sig. below. I downloaded and tested the AMD64-Mac ISO and it booted up beautifully and EVERYTHING worked out of the box.  I'm wondering if I can install Ubuntu on a separate drive cleanly and not disturb the OSX drive?  I won't if it would install this way and run without the OSX drive installed.  Does it read the EFI on the boot drive before booting to the CD image I tried.  I may experiment with this down the road, but I don't feel like being a Guinea Pig right now.

If anyone knows for sure let me know too.  Thanks to the OP for posting this question.

---

### Post by rmorr on 2013-03-23
It's probably not much more complicated than making sure you bless the Ubuntu boot loader before you delete OS X; or keeping around OS X on a thumb drive and doing Ubuntu as a single install and using the thumb drive to bless your boot loader. The only question, I think, would be whether you've got Ubuntu installed in EFI or BIOS mode ... but that is just going to change what you bless.

---

### Post by rmorr on 2013-03-23
Here you go -- from the terminal w/ either your OS X install before you erase it or from a thumb drive or install CD. And you can test either of these methods without uninstalling anything. I'd do it myself and report back but I'm using rEFInd to load the kernel directly from my efi:

EFI (something close to this) -- where grub2 is renamed bootx64 or 32 (depending on your architecture) .efi:

mkdir /Volumes/esp
sudo mount -t msdos /dev/disk0s1 /Volumes/esp
sudo bless --mount /Volumes/esp --setBoot --file /Volumes/esp/EFI/Boot/bootx64.efi 

BIOS Install ("X" where "X" is the drive holding grub):

sudo bless --device /dev/disk0sX --setBoot --legacy

---

### Post by este.el.paz on 2013-03-24
> **crjackson said:**
> This is exactly my question too.  I just got a new (my first) Mac Pro listed in my sig. below. I downloaded and tested the AMD64-Mac ISO and it booted up beautifully and EVERYTHING worked out of the box.  I'm wondering if I can install Ubuntu on a separate drive cleanly and not disturb the OSX drive?  I won't if it would install this way and run without the OSX drive installed.  Does it read the EFI on the boot drive before booting to the CD image I tried.  I may experiment with this down the road, but I don't feel like being a Guinea Pig right now.

If anyone knows for sure let me know too.  Thanks to the OP for posting this question.

@crjackson:

The fact that the .iso booted and worked is probably a good sign that an install would go well.  I think that if you add another HD and just use the installer to install a single system into it would not require any extra effort . . . the installer would set it up for you.  And then to switch HDs it would be just like selecting an external HD linked by FW to boot into--just hold "option" key down and the boot selector window will show the available systems . . . .  If it doesn't work there is always SuperGRUB2 to use to boot systems . . . .

e.e.p.

---

### Post by crjackson on 2013-03-24
> **este.el.paz said:**
> @crjackson:

The fact that the .iso booted and worked is probably a good sign that an install would go well.  I think that if you add another HD and just use the installer to install a single system into it would not require any extra effort . . . the installer would set it up for you.  And then to switch HDs it would be just like selecting an external HD linked by FW to boot into--just hold "option" key down and the boot selector window will show the available systems . . . .  If it doesn't work there is always SuperGRUB2 to use to boot systems . . . .

e.e.p.

I'll probably give this a try later this week.  If it will work out as you have described, that would be perfect.

---

### Post by este.el.paz on 2013-03-24
> **crjackson said:**
> I'll probably give this a try later this week.  If it will work out as you have described, that would be perfect.

Cool.  Hopefully you understood that the "holding the option key down" meant holding the option key after a system restart, not just pushing the option key while booted in OSX, sorry if that wasn't clear . . . or sorry for this post if you already knew that.  But, there should be plenty of other stuff to do with your new computer . . . on OSX . . . unless you have another HD just sitting around ready to be clicked into place . . . .  But, either way, post back to the thread with how things go, it might help somebody else . . . .  In a few months I'm looking for a new desktop, one that I hope to be able to have a couple HDs in so I don't have to partition a drive, etc.

e.e.p.

---

