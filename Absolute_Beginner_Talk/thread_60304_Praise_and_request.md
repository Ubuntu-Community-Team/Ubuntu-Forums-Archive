---
title: "Praise and request"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by DaveRowell on 2005-08-27
First off - the developers and documentation folks HAVE done a great job in making a (more-or-less) newbe-user friendly desktop distribution.  Hardware detection seem s flawless things just work.  Partitioning works well.  Thanks.

More work is needed to address some problems unique to some modern PC's: 
 1 -  most PC's don't have floppy drives anymore - they've been "replaced" by flash drives on USB ports and rewritable optical drives which give a LOT more capacity
 2 - several PC manufacturers (HP, Compaq ...) have a propriatary boot loader linked to a closed boot/recovery first partition.  The associated drive letters are swapped after Windoze XP loads.
     This leads to some serious Linux install problems - replacing the boot loader (which is the default on all Linux distros I've tried) essentially trashes the mfg's recovery/boot scheme.  Doing it the "right" way requires installing the boot loader on the Linux boot partition, making a boot floppy, copying the 1st boot partition sector to a fat drive and then incorporating that file into Win XP's boot loader.  BUT without support for USB drives (or cards in USB card readers) or NTFS that's difficult or impossible (I'm not sure which yet  :roll: )
     Replacing that propriatary boot loader has serious repercussions - the whole system is trash!  The first partition no longer has the boot code - most of it (but not all?) is on the second partition.  I know that FDISK /MBR won't fix it and I didn't find any way to fix it.  The distro that I installed to screw-up my system wouldn't even boot!  [NOT a current problem]

So here I sit with ubuntu 504 installed on its partition - GRUB installed on nothing (it didn't install on my CF card, sdc1) - with no way to boot ubuntu.  I don't know enough to figure out how to recover using the live CD.  Ideas?

---

### Post by void_false on 2005-08-27
Thats why i never buy brand!!!  ](*,)

---

### Post by banjo04414 on 2005-08-27
Get partition Magic 8.0 with Boot Loader. After you install Ubuntu go back to Windows and run Partition's Boot loader. Then it will run OK and not mess up your MBR. If you decide you want just the orginal MBR, turn off Partiton Magic Boot Loader. :grin:

---

### Post by numberexhaust on 2005-08-27
You could try playing around with the tool "qtparted" that is built into Knoppix.  It is essentially a port of Partition Magic.  I've personally never had to use it but I heard it was pretty good.

Another option is to try to recover via install another OS ( :shock: ).  I had a big problem with my partition table (after installing a form of FreeBSD) and the way I ended up recovering it was by installing SuSE.  They, for some reason have a good way of detecting and taking care of partitions.  I remember at that time no other distros would even go into the install process, but SuSE took the whole thing perfectly.  Of course, afterwords I wrote that over with my Ubuntu  ;-) .

Hope that helps.  Reply here if U have any other questions.

---

### Post by numberexhaust on 2005-08-27
[QUOTE=banjo04414]Get partition Magic 8.0 with Boot Loader. After you install Ubuntu go back to Windows and run Partition's Boot loader. Then it will run OK and not mess up your MBR. If you decide you want just the orginal MBR, turn off Partiton Magic Boot Loader. :grin:[/QUOTE]
 Try my qtparted idea first... mainly because it's free!

---

### Post by banjo04414 on 2005-08-27
By all means you should try QtParted. However, if that doesn't work out-PM's Bootloader is worth the money as it let's you have many OS on one,two or three HD's. It's just another option. hope this helped you.

---

### Post by Brunellus on 2005-08-27
[QUOTE=DaveRowell]First off - the developers and documentation folks HAVE done a great job in making a (more-or-less) newbe-user friendly desktop distribution.  Hardware detection seem s flawless things just work.  Partitioning works well.  Thanks.

More work is needed to address some problems unique to some modern PC's: 
 1 -  most PC's don't have floppy drives anymore - they've been "replaced" by flash drives on USB ports and rewritable optical drives which give a LOT more capacity
 2 - several PC manufacturers (HP, Compaq ...) have a propriatary boot loader linked to a closed boot/recovery first partition.  The associated drive letters are swapped after Windoze XP loads.
     This leads to some serious Linux install problems - replacing the boot loader (which is the default on all Linux distros I've tried) essentially trashes the mfg's recovery/boot scheme.  Doing it the "right" way requires installing the boot loader on the Linux boot partition, making a boot floppy, copying the 1st boot partition sector to a fat drive and then incorporating that file into Win XP's boot loader.  BUT without support for USB drives (or cards in USB card readers) or NTFS that's difficult or impossible (I'm not sure which yet  :roll: )
     Replacing that propriatary boot loader has serious repercussions - the whole system is trash!  The first partition no longer has the boot code - most of it (but not all?) is on the second partition.  I know that FDISK /MBR won't fix it and I didn't find any way to fix it.  The distro that I installed to screw-up my system wouldn't even boot!  [NOT a current problem]

So here I sit with ubuntu 504 installed on its partition - GRUB installed on nothing (it didn't install on my CF card, sdc1) - with no way to boot ubuntu.  I don't know enough to figure out how to recover using the live CD.  Ideas?[/QUOTE]
 I was concerned about this when I set up my Ubuntu/WinXP dualboot machine.  My concerns ended up being without merit.  GRUB loaded itself onto the MBR and, on startup, gives me my choice of kernels--Ubuntu (x86), Ubuntu (k7), WinXP, and the Win XP recovery partition.

The one known way to mess this up is to attempt to reinstall Windows on top of an existing Ubuntu instatllation--Windows trashes the MBR with its own bootloader, and you're left with an unbootable linux system, but all the windows you can stand.

---

### Post by DaveRowell on 2005-08-28
"**void_false**" suggested that my problem is related to the purchase of a brand name machine - probably so.  However, last winter I was going to build a simple little box that would have had a parts price (NewEGG) of around $1200 including a bottom line 15" LCD.  I got this Compaq [AMD Athlon 3200+, 512 MB RAM, fast 120 GB HD, CD-R/W, DVD ROM, kbd, mouse and a pretty nice 17" LCD monitor] for under $900! at Sam's Club.  Processor 1 bin faster, same RAM, same drive, much better monitor, mouse & kbd, instead of the 2 optical drives I would have had a single DVD-R/W.  BUT I still wouldn't have had a floppy drive.

Untill the warranty runs out I'm not going to get rid of the Compaq baggage.  I may not then unless I decide to go with Linux as a sole operating system or upgrade to Windoze XXXX when it launches.  

Unless the application picture changes radically I can't use Linux exclusively:
 - can't afford a good 2d/3d CAD to replace the CADKEY I have now
 - can't find a genealogy program as good as what I have now (I have tried GRAMPS and its OK but not as good as PAF5 or Ancestral Quest)
 - I write and use design software in MS Prof Basic (works well under XP) and I don't see a good replacement under Linux (Yes, I've coded a few applications under GCC and it works well but don't really want to change all this stuff)
 - I think that GIMP will do everything that Paint Shop Pro will do
 - all my CD's are on line as MP3 files reformating them would be a PIA
 - I'm not sure about viewing or editing video under Linux

I'm pushing 70, been programming since the late '60's and the Linux learning curve is giving me the willies!  Yes it has superior features.  Yes it gives MS some competition which they sorely need.  But Windoze works well for this individual's personal desktop - Linux doesn't as yet.

As I see it UNIX failed to compete with MS because it was fragmented - every mfgr has its own version - while wintel PC's all use the same MS operating system.  Apple tried to keep everything propriatary and expensive.  Untill recently the MS operating system was reasonably priced.  The result has been complete dominance of the user desktop.  Howm many Linux distro's are there?  All trying to claim my desktop!  Hmmmm, I wonder if things would be better in the Linux world if the developers could just concentrate on a single distro or at least try to make them all use the same updating methedology and the same application packages?????

---

### Post by numberexhaust on 2005-08-28
Well what I've found with linux, to give you some encouraging advice, is to just install it, boot into it, and play.  Everything else will come with time.  :D  Don't ever be discouraged if something doesn't work.  If you want everything to work right out of the box perfectly, just buy a mac.  But that would take all the fun out of it, wouldn't it?

---

### Post by racecat on 2005-08-28
All of this reminds me of my approach to diving into Linux. I wasn't willing to chance comprimising my preloaded XP box, but I really wanted to work with Linux.

Solution: buy a used pc. They are cheap and plentiful and you get extra benefits:
1you get a chance to play with networking
2 networked boxes are a natural for backing up important files
3 no rebooting to get to the os that's not up

add a $20 kvm switch, and you're not even taking up more desk space

Anyway, that was my approach. I'm kind of conservative (by nature and necessity), so I don't have lots of money invested. That's a great thing about Linux - cutting edge software that will run on older machines. It's a beautiful thing.

Happy trails,
Bill

---

### Post by banjo04414 on 2005-08-28
[QUOTE=DaveRowell]"**void_false**" suggested that my problem is related to the purchase of a brand name machine - probably so.  However, last winter I was going to build a simple little box that would have had a parts price (NewEGG) of around $1200 including a bottom line 15" LCD.  I got this Compaq [AMD Athlon 3200+, 512 MB RAM, fast 120 GB HD, CD-R/W, DVD ROM, kbd, mouse and a pretty nice 17" LCD monitor] for under $900! at Sam's Club.  Processor 1 bin faster, same RAM, same drive, much better monitor, mouse & kbd, instead of the 2 optical drives I would have had a single DVD-R/W.  BUT I still wouldn't have had a floppy drive.

Untill the warranty runs out I'm not going to get rid of the Compaq baggage.  I may not then unless I decide to go with Linux as a sole operating system or upgrade to Windoze XXXX when it launches.  

Unless the application picture changes radically I can't use Linux exclusively:
 - can't afford a good 2d/3d CAD to replace the CADKEY I have now
 - can't find a genealogy program as good as what I have now (I have tried GRAMPS and its OK but not as good as PAF5 or Ancestral Quest)
 - I write and use design software in MS Prof Basic (works well under XP) and I don't see a good replacement under Linux (Yes, I've coded a few applications under GCC and it works well but don't really want to change all this stuff)
 - I think that GIMP will do everything that Paint Shop Pro will do
 - all my CD's are on line as MP3 files reformating them would be a PIA
 - I'm not sure about viewing or editing video under Linux

I'm pushing 70, been programming since the late '60's and the Linux learning curve is giving me the willies!  Yes it has superior features.  Yes it gives MS some competition which they sorely need.  But Windoze works well for this individual's personal desktop - Linux doesn't as yet.

As I see it UNIX failed to compete with MS because it was fragmented - every mfgr has its own version - while wintel PC's all use the same MS operating system.  Apple tried to keep everything propriatary and expensive.  Untill recently the MS operating system was reasonably priced.  The result has been complete dominance of the user desktop.  Howm many Linux distro's are there?  All trying to claim my desktop!  Hmmmm, I wonder if things would be better in the Linux world if the developers could just concentrate on a single distro or at least try to make them all use the same updating methedology and the same application packages?????[/QUOTE]
  I feel your pain. However, check out the How To. They have a nice summary on how to recover Ubuntu. Also, "Windows" has the recovery console on your cd. No need for a second desktop IMO. After you straighten out this first hurdle, just take your time learning Linux[Ubuntu}. It is really a very good OS. As a last resort, HP has a good record of customer support. I just purchased their SR1536NX. I have always built my own from scratch, but it seems today you get so much more from these "packaged" systems.

P.S. Beowse thru the forum, many iother people have the same problem-Good Luck

---

### Post by DaveRowell on 2006-03-08
OK, so here I sit some 6 months later - Ubuntu has been my default log-in for several months now - I'm reasonably happy.  :)  As suggested I just gritted my teeth and dove in.

I've stirred up my hard drive in a big way.  Shrunk XP's share big time - made a FAT32 partition for common data - made a separate /home partition.  After Dapper is a couple of months old I'll update - maybe a fresh install, who knows?

I CAN play MP3's.  I CAN watch movies in many different encoding formats.

There have been (and  continue to be) a few bumps in the road but many kind souls have given me a nudge in what turned out to be the right direction.

Wine has been a help - what a fine bunch of folks there :-D  As I've found good Windoze apps that run I've been adding them to the application database.

Recently I've logged into XP quite a few times to run some of the web related functions of Ancestral Quest genealogy program.  Primarily AQ runs on my Win98SE notebook with the majority of the data on a 1/2 gig pen drive.  That's the only reason I run XP anymore.

---

### Post by Mustard on 2006-03-08
It's great to read of your progress.  Thanks for coming back and replying. :)

---

### Post by Karisson on 2006-03-08
[QUOTE=numberexhaust]Well what I've found with linux, to give you some encouraging advice, is to just install it, boot into it, and play.  Everything else will come with time.  :D  Don't ever be discouraged if something doesn't work.  If you want everything to work right out of the box perfectly, just buy a mac.  But that would take all the fun out of it, wouldn't it?[/QUOTE]

Agreed. I had a hard time starting out with Ubuntu, but after a while you get used to it. It's not altogether too much harder to use than Windows, it just takes a little time to get the hang of it.;)

---

### Post by DaveRowell on 2006-03-09
Yeah, I guess we tend to forget that Windoze crept up on us over a period of years.  With Ubuntu it all came at once!

---

### Post by mstlyevil on 2006-03-09
Glad to see things are working out for you. Ubuntu was my first Linux distro and this community is what makes all the difference. Thanx for the update, it was very inspiring.

---

