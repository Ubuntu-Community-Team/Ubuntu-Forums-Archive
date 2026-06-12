---
title: "Ubuntu Success Story"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by hoarsecourser on 2007-01-22
Hello All.  I just thought I'd share with you some trials and tribulations in my most recent install of Ubuntu.

The story begins with the death of a Sony Vaio (PCG-R505GL) laptop that was happily running Dapper for a few weeks.  The death was totally my fault (I killed some hardware).  Regardless, it left me without a linux box.  So...I have an external USB hard drive...an XP laptop (Acer Aspire 5560 [from Taiwan])...and a bunch of Linux installation CDs lying around...

From setback to setback:  Turns out my internal DVD-RAM drive has decided not to read anything, despite it being properly detected and the drivers being up to date...possibly a hardware problem, but I wasn't about to take apart (and likely kill) another laptop this week.  Off to the store for an external DVD burner...(because of all my previously failed attempts to load a CD image onto the external HDD or get a bootloader onto it).

*a careful reader will not my refusal to mess with the bootloader on my XP machine...paranoid is all*

So, in goes the Edgy install/Live CD.  Fire up the machine...press F12 to select boot drive...select USB CD drive...and up it goes.  Great!  Open up installer program...choose language, time zone, keyboard layout...Select drive.  Now I know that the external HDD is only 40G, while the internal is 100G, so that's easy to choose.  Automatically partition (erase entire disk [it was blank already]) then on to the final screen.  Oops!  What's this?  GRUB is going to hd0...I don't like that at all...so I change it to my external disk.  Should be good, right?  Click install...partitioner starts up...halts at 15% of first partition being made.

Repeat above paragraph two more times (I just wanted to be sure).  Hmm...Repeat above paragraph, replacing Dapper for Edgy.  Erase all mentions of GRUB going to hd0 (no GRUB placement options in Dapper installer).  Now change "halts at 15%..." to "completes install with no problem whatsoever"  Hoo-Freakin-Rah!  Boot it up a few times...runs great...curiosity sets in...

I wonder if the HDD from the Vaio will boot up...long-story-short: No (don't know why).

So here I am posting to this forum while the Distribution Upgrade runs, thus upgrading from Dapper to Edgy (see other posts on how to do that if you're curious)...and if it doesn't work...back in goes the Dapper Live/Install CD.

In closing: Hooray for Ubuntu...I now have a harddrive/OS that I can let my teenage child use the internet on without fear of messing with my box (as Ubuntu can't mount the NFTS drive that's inside the laptop)...a second computer for the price of spare parts (and a new external DVD burner...but that was just me).

---

### Post by steven_mckenz on 2007-01-22
Yeah, I'm not entirely sure with the automatic install of the grub loader to hda0.

When I installed it on my system, I used a Sata drive.  It autodetected the sata drive and everything, but then it told me that it was going to install the loader to hda0, instead of sda0.  I had no idea why the hell it wanted to do that, as I didn't even have a PATA drive in my system!  But I said "oh, what the hell" and let it do it anyway, just to see what happened, and lo' and behold, it booted right up, installed just fine, and has been working ever since.

Who knows!  :cool:

---

### Post by hoarsecourser on 2007-01-22
Yeah, I was totally unsure about the GRUB thang...so I avoided it.  I'm still running the distribution upgrade (really slowly) so we'll see what happens with that.  Here's hoping!  Does anyone else know what happens with the GRUB loading to (hda0) and if that will affect the partitioner's operation?

---

