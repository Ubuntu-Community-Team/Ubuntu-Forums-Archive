---
title: "Is my partition table gone?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by BooUrns on 2007-10-05
I'm completely new to Linux, and I just installed Ubuntu 7.04 alongside Vista Business.  Vista shows up in GRUB, but it crashes whenever I try and start it.  I've looked around and found that other people have also had this problem.  I have tried various solutions, with no success so far.

One thing I tried was ntfsfix, but I can't seem to find the Windows partition name.  In fact, I think the entire partition table has disappeared.  When I boot the GParted LiveCD, it shows me that my entire hard drive is unallocated space.

I'm very new and very confused, so could someone tell me what on earth has happened to my partition table and if there's a way to get it back?  I'm locked out of Vista until then... (which I suppose isn't nessecarily a bad thing :wink:)

---

### Post by dcstar on 2007-10-05
> **BooUrns said:**
> I'm completely new to Linux, and I just installed Ubuntu 7.04 alongside Vista Business.  Vista shows up in GRUB, but it crashes whenever I try and start it.  I've looked around and found that other people have also had this problem.  I have tried various solutions, with no success so far.

One thing I tried was ntfsfix, but I can't seem to find the Windows partition name.  In fact, I think the entire partition table has disappeared.  When I boot the GParted LiveCD, it shows me that my entire hard drive is unallocated space.

I'm very new and very confused, so could someone tell me what on earth has happened to my partition table and if there's a way to get it back?  I'm locked out of Vista until then... (which I suppose isn't nessecarily a bad thing :wink:)

There are utility boot CDs around that allow you to examine and repair (if you know what you are doing) partition tables - I think one is called "Ranish" (a web search should reveal some info).

---

### Post by molly_001 on 2007-10-05
The utility bootable CDs to repair partition tables are not often successful, in my opinion.

I'd recommend acquiring the media for installing your version of Vista, then reinstalling Vista on a newly formatted drive.  (That is to say, use the Vista installation CD to 'slow' format a partition of the hard drive -- size perhaps 50% of the drive maximum.)

Then install Vista on that partition.

Then use Alternate Install CD of Ubuntu 7.04 (not Live CD) to install Linux afterwards.  (for dual boot)

---

### Post by indytim on 2007-10-05
Or, to take all of the guess-work out of the equation, use GParted Live to set up your /swap and ext3 partitions before installing Ubuntu.  Record the location of the above.  When you come to the partition section of the install, opt for the manual install and designate the apprppriate partitions for  "/" and /swap.

Good Luck,

IndyTim

---

