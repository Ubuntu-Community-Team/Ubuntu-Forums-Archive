---
title: "Grub error 18 only with Gutsy dual-boot"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Jay80 on 2008-03-10
For a long time I had a dual-boot install with Windows and secondly Ubuntu Dapper Drake (on a single
smallish 80 GB drive),  and it ran OK with no problems at all, no Grub error messages.  To replace 
Dapper with Gutsy 7.10, I first returned the MBR to Windows only, then used PMagic to delete the
Dapper partitions and installed Gutsy 7.10 as dual-boot. No problems with the install procedure, and
Grub initially displayed its boot menu and allowed booting to either Windows or Gutsy;  however,
soon Grub  intermittently began stalling with the "Error 18" message. Sometimes rebooting would fix
this, sometimes not. I did several removals and both auto and manual reinstalls, but the Grub Error 18
problem persisted.

As dual-boot had  previously worked OK with Dapper Drake, I wondered if this Grub error was due to
a bug in the current Gutsy release, so as an experiment I again removed Gutsy and did a dual-boot
install with Linux Mint 4 in its place. This works OK with no Grub error messages.

Is this a known bug with Gutsy, or should I report it as a bug?  Seems to me that either this version
of Grub has a bug, or Gutsy is not handling it correctly.

I tried searching the forums, but maybe I don't know the trick with the search button - no matter
what I search for, it gives no results found even though I enter a term that I know exists in some
of the posts.

---

### Post by forrestcupp on 2008-03-10
I wonder what would have happened if you would have just reinstalled Gutsy instead of Mint 4.  That may have taken care of your problem, too.  I have never had trouble with Grub like that.

But for future reference, you don't have to jump through all of those hoops to upgrade your Ubuntu version.  You could have just run the Gutsy installation and done a manual partition in the installation and formatted and reused your Dapper partitions.

But I suspect there's more to the story.  It sounds like at one time you decided to give up on Linux and go back to Windows.  Then you changed your mind and came back.  I've done that myself.

If you like Mint, you might as well stay with that.  It is a good distro, and it's pretty much Gutsy with an overhaul and extra stuff installed.  The only downside to it is that they don't have a 64-bit version yet.

---

### Post by louieb on 2008-03-10
Just wondering how old is the PC?  If the PC was made in the 1990's then its BIOS could be the cause of the grub error 18. 
This is the one case where a separate  /boot partition toward the front of the drive is the workaround. Grub error 18 is the only reason I would make one.   [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

It could be you just got lucky with Dapper and Linux mint  - the stage2 program and kernel were stored within the  BIOS boot limit.

---

