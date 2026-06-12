---
title: "Boot prblem fixed, I think"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-04-13
It seems that editing my fstab & mounting all my HD's has fixed my boot up problem.
I would have thought fstab wasn't read by the OS until after you log in but I guess it does.  To rehash the problem.
Every time I would boot up the computer for the first time into Edgy after it was off for for a while, it would lock up completely. It would never get to the login screen. I'm dual booting but I didn't have the problem if I booted first to Windows. I could restart O.K. from windows or Edgy it was only on first cold boot.  I've got 3 HD's & since I've got them mounted & they show up on my desktop everything has been fine.
Any theories?

---

### Post by Vladimirm on 2007-04-13
/etc/fstab is read at boot not at login.

Do you meed help with an existing problem? or is everything ok now?

---

### Post by freebird54 on 2007-04-13
I have experienced similar things on many systems with various OS's.  IT is caused by an insufficient delay for the hard drives to spin up and acknowledge their presence/readiness in time.  IT happened most often with SCSI drives in the past (especially those that spun up to 10,000 rpm) but no type was immune.  Occasionally you come across it with an aging drive that becomes a bit temperature sensitive, and needs to be warm to function correctly.  The only cure for those is 1) back it up and 2) don't power down!  That can keep things running for 2 years more in some cases.

Summary?  Probably hardware - perhaps one of  the drives gets the start signal too late ( probably a slave drive - or one hooked up another way like USB)

EDIT:  Another workaround is to reboot just after the prompt for BIOS setup has been displayed - to give the drives that extra time/temperature...

---

### Post by garyed on 2007-04-13
Everythin g seems O.K. now.
I posted about this problem before here & didn't get any responses so I figured it would be a good idea to post what probably fixed it.

---

### Post by garyed on 2007-04-13
> **freebird54 said:**
> I have experienced similar things on many systems with various OS's.  IT is caused by an insufficient delay for the hard drives to spin up and acknowledge their presence/readiness in time.  IT happened most often with SCSI drives in the past (especially those that spun up to 10,000 rpm) but no type was immune.  Occasionally you come across it with an aging drive that becomes a bit temperature sensitive, and needs to be warm to function correctly.  The only cure for those is 1) back it up and 2) don't power down!  That can keep things running for 2 years more in some cases.

Summary?  Probably hardware - perhaps one of  the drives gets the start signal too late ( probably a slave drive - or one hooked up another way like USB)

EDIT:  Another workaround is to reboot just after the prompt for BIOS setup has been displayed - to give the drives that extra time/temperature...

I don't think in my case it was a hardware problem.
If it was a hardware problem I wouldn't think it would make a difference booting into Windows or Linux but it did, or editing fstab which it also did.
I do think you're right about it having to do with HD access because it would start to load & get to the Ubuntu logo & then stop all HD access. It was like the OS didn't know where to look.

---

### Post by garyed on 2007-04-13
Well I was wrong, my boot problem still exists.
I've had the computer off since my last post & just got home from work & it locked up again at boot-up. I can reset it now & it will boot up fine. Again it only does it booting into Edgy.

---

### Post by freebird54 on 2007-04-13
Does waiting a little make a difference?  It could be that the Edgy drive is the one with the startup or temperature issue.  (the temperature issue seems to be regarding things written with the internals at high heat being misaligned slightly on a track to track basis when the internals are cold.  This happens more frequently now that tracks and heads are so small).  As I mentioned - leave it on, or switch which physical drive does which job.  Another thing thing that can be checked is the airflow on that particular drive - often leads to the problem in the first place!

Unfortunately, changing which drive does what is the only way to be sure of this, so it can mean a lot of backing up/re-installing or imaging or...

Good luck with this - and happy to help with ideas on workarounds if you decide to try them (other than just leaving it powered up - and keeping good backups!

---

### Post by garyed on 2007-04-13
> **freebird54 said:**
> Does waiting a little make a difference? ........... 

Actually the longer I leave the machine off the more chance it has to lock up so i don't think its a heat issue. Going back to your original response it may be a time issue since windows takes a lot longer to boot up than Linux & I never have the problem booting to windows, nor do i have a problem restarting from Windows to Linux or Linux to Linux.
Linux is on a partition on my IDE 1 slave drive   
IDE 1 - Master -Win98 OS
IDE 1 - Slave -  Linux + Windows/files
IDE2 - Master - Windows/files
IDE2 - Slave - DVD

---

### Post by freebird54 on 2007-04-13
> Actually the longer I leave the machine off the more chance it has to lock up so i don't think its a heat issue.

Actually - that is exactl;y the behaviour to be expected with a heat issue. The colder it gets - the more likely to be 'off the track' the R/W head is.  The effect varies across the drive as well - it is usually more critical towards the centre of the drive.  This means that the newer the item is, the more likely it is to have difficulty being read while cold.  The stuff that went on when the system was newer is less likely to be a problem.

In this case, if your Ubuntu is on the same drive, the best fix might be to make room on another drive for your boot/root Linux partition - Linux doesn't even require one of the 4 primary partitions to boot! (extended is fine).  Just a suggestion...

---

