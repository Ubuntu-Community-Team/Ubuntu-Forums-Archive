---
title: "subprocess /usr/bin/dpkg returned an error code (1)-Xubun 12.04/iMac800"
date: 2017-06-17
forum: Apple Hardware Users
---

### Post by este.el.paz on 2017-06-17
Folks:

It's been awhile since I've posted here, as the life slowly drains out of PPC there has been less reason or need . . . .  A year or more back my long lived iMac 800 started "kernel panicing" and it seemed like some mobo issues that couldn't be fixed after much effort I finally unplugged it and set it down on the dusty floor with the other graveyard items . . . .

Yesterday I thought I'd try to pull the HD before I took the machine to a recycler, and before I did that I plugged it in and booted it up . . . crashed in OSX again right away.  Trying to get applejack to load I booted into OSX single user and it said something about "SuperDrive not recognized" . . . no applejack.  So I shut it down and rebooted to set the PRAM for 6 chimes and the yaboot window loaded and I tried the Xubun 12.04 install that rsavage posted waay back when . . . and there were some crash reports "application dpkg has closed unexpectedly" . . . and it gave me the hint to "try -f install" . . . so I did that and it showed "312 packages to install" . . . so I ran that, and at the end was something about "dpkg" with an error of "subprocess /usr/bin/dpkg returned an error code (1)" . . . .

I ran through various "apt-get upgrade -f install" variations . . . and the console would say "dependencies fixed" . . . go through a few more lines, but still find the same error code, and still showing that the "312 packages" were waiting to be installed . . . so obviously were not, due to this dpkg error . . . ???

So, I'm typing this post in the iMac, which previously the machine would only run for a few minutes, even in linux . . . so, having given this machine up for dead a long while back I haven't been paying attention to what's left in PPC-land, . . . I've noticed on my G4 iBook running Lu 16.04 that some of the "apt updates" lines bring errors . . . so likely not all of the packages are available in PPC?  In one of the attempts to get the iMac going in Xu there was a console error of "apt-cdrom cant recognize the cdrom" . . . and I used apt --autodetect . . . and later I was able to try to boot a ubuntu live DVD . . . but, long since forgotten the boot params needed to get video . . . .

Should I try to run "apt-get install dpkg"   and see if that does anything??  Or, any commands to run that will repair dpkg ???

Thanks,

e.e.p.

---

### Post by ernsteiswuerfel on 2017-06-18
> **este.el.paz said:**
> It's been awhile since I've posted here, as the life slowly drains out of PPC there has been less reason or need . . . . A year or more back my long lived iMac 800 started "kernel panicing" and it seemed like some mobo issues that couldn't be fixed after much effort I finally unplugged it and set it down on the dusty floor with the other graveyard items . . . .
Old PPC (and 680x0) Apple gear is legacy hardware and should be taken care of with the same effort other people put in their Retro-Systems. At least if you want to run your hardware for another decade. ;) Even if the Apple PPC-machines are the most 'modern' machines and are usable for common tasks by todays standards. Harddisks fail, fans fail, thermal paste drys out, motherboards are collecting statically loaded dust, capacitors leak... You need to do some maintainance. Changing fans, harddiscs, PRAM battery, applying new thermal paste is easy, for other tasks like repairing the water cooling system of a G5 quad or for resoldering you need experts.

If such tasks annoy you, you could buy new PPC-hardware ([klick]("http://amigakit.leamancomputing.com/catalog/product_info.php?products_id=1303")), hopefully a new PPC-Laptop ([klick]("https://www.powerpc-notebook.org/en/")) will be available in 1-2 years.

Easiest solution of course would be to buy cheap 2nd hand standard x86-hardware and run 32/64bit x86-Ubuntu on it. But keep in mind that even x86-gear should not be too old, or you will face more or less the same issues as on your Apples. The Xorg-driver for an ATI Rage 128 from 1999 is exactly the same, regardless if it sits in a G4 PowerMac ore some x86-AGP-mainboard. ;)

> In one of the attempts to get the iMac going in Xu there was a console error of "apt-cdrom cant recognize the cdrom" . . . and I used apt --autodetect . . . and later I was able to try to boot a ubuntu live DVD . . . but, long since forgotten the boot params needed to get video . . . .
For some of the common boot parameters see my post [here]("https://ubuntuforums.org/showthread.php?t=2363952"). Debians PowerPC-FAQ has some info too ([klick]("https://wiki.debian.org/PowerPC/FAQ")).

> I've noticed on my G4 iBook running Lu 16.04 that some of the "apt updates" lines bring errors . . . so likely not all of the packages are available in PPC?
Normally Ubuntu only shows packages for the architecture your machine has. Unless you manually editet the sources.list. See [here]("https://help.ubuntu.com/community/Repositories/CommandLine").

> Should I try to run "apt-get install dpkg" and see if that does anything?? Or, any commands to run that will repair dpkg ???
You don't need to install *dpkg* as it's already on your machine. *apt-get* is only a wrapper of dpkg. If the package tree is badly broken, you need to fiddle with dpkg itself. Look [here]("http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/") for a good and short guide. Or search the Ubuntu/Debian forums for 'dpkg fix broken installation', that's non Apple/PPC-specific.

---

### Post by este.el.paz on 2017-06-18
> **ernsteiswuerfel said:**
> 

For some of the common boot parameters see my post [here]("https://ubuntuforums.org/showthread.php?t=2363952"). Debians PowerPC-FAQ has some info too ([klick]("https://wiki.debian.org/PowerPC/FAQ")).

Normally Ubuntu only shows packages for the architecture your machine has. Unless you manually editet the sources.list. See [here]("https://help.ubuntu.com/community/Repositories/CommandLine").

You don't need to install *dpkg* as it's already on your machine. *apt-get* is only a wrapper of dpkg. If the package tree is badly broken, you need to fiddle with dpkg itself. Look [here]("http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/") for a good and short guide. Or search the Ubuntu/Debian forums for 'dpkg fix broken installation', that's non Apple/PPC-specific.

@ernsteiswuerfel:

Thanks kindly for the reply and for the links . . . after I posted I recalled that I probably posted some boot params on the forum here a few years back on the "12.04 for dummies" thread . . . but, I'll check what you've linked . . . I recall for the iMac there was some "@ xx" for the horz/vert refresh . . . I have all this data written down on yellow legal pads, but not organized, just piled in stacks of "daily diary" notes . . . .  : - 0

And, right, only showing packages in the sources list, but for some months now all my PPC systems have been showing a "not found" error on some lines . . . .

And, right, dpkg is obviously installed, but it is showing up as an error, and it seems to not be doing its job of completing the install of upgrades . . . as it keeps cycling through the same list of "to be installed" packages . . . which aren't being installed . . . only to "find" them again . . . appear to be "installing" but, then the install errors out with the line in the thread subject header here . . . .  I'll try to look into the linked commands you provided in the coming days . . . we'll see what happens . . . .

e.e.p.

---

### Post by ian-weisser on 2017-06-19
dpkg 'error code (1)' simply means "a common reason". Like a simple failure in a post-install script. Or out-of-space. Generally easy to fix...when you understand the complete error message. 

Since you have not shown us the complete error messageyet, not much more help we can provide.

---

### Post by este.el.paz on 2017-06-19
> **ian-weisser said:**
> dpkg 'error code (1)' simply means "a common reason". Like a simple failure in a post-install script. Or out-of-space. Generally easy to fix...when you understand the complete error message. 

Since you have not shown us the complete error messageyet, not much more help we can provide.

@ian-weisser:

Thanks for the response . . . well, that was the more or less the "complete" error message that showed up at the "end" of one of a series of attempts to run "update/upgrade" that failed . . . .  Other than the crash report info, but, after a couple crash reports there was something like, "we can't do any more crash reports on this system" message.  In the console there hasn't been a whole lot of detailed info . . . the actual problem is that the console keeps cycling through "installing" the upgrades . . . but, fails or errors out of that process . . . w/o much explanation, and even seeming to "think" that it has "done a good job" . . . but, reloading the same packages again as "downloaded but not installed" . . . over and over.

Haven't had the time to go through on ernst's suggested commands yet to see if that cleans anything up . . . or not . . . .

e.e.p

---

### Post by ian-weisser on 2017-06-19
What you have shown us is merely a summary, not the actual error message at all..
You must show us the ENTIRE output of an apt upgrade for us to help you usefully. The real error message is usually in that output.

---

### Post by este.el.paz on 2017-06-20
> **ian-weisser said:**
> What you have shown us is merely a summary, not the actual error message at all..
You must show us the ENTIRE output of an apt upgrade for us to help you usefully. The real error message is usually in that output.

@ian:

OK, went through the update/upgrade process again and copy/pasted it into a doc . . . however, I've tried to upload the roughly 17kb .odt &/or compressed to tar.gz file using the "attachments" window numerous times in both the iMac and then a newer MacPro, the little gear wheel spins and then stops, but no attachment makes it to the forum.  Should I just paste the contents into a post ??  Or, is there some server problem with the attachments window?

e.e.p.

---

### Post by este.el.paz on 2017-06-20
OK, had to switch over to OSX to get the attachment to upload in FF . . . so there is the latest update/upgrade console report . . . I ran through the "cdrom" commands the other day, didn't seem to "take" . . . and same thing with the "310" packages "not upgraded" . . . ran through that a few times, seems like now it isn't bothering to try to"install" them . . . .  Also "interesting" this is a base Xubuntu PPC 12.04 install, but the cdrom error is showing "Lubuntu" . . . which I probably have as an added DE . . . to the Xubuntu install.

Computer is "running" OK in spite of the crash reports and the international red circle with the horz white line . . . it's just "slow" in what it does, and, couldn't seem to succeed in uploading the .odt file to this forum . . . .

e.e.

---

### Post by ian-weisser on 2017-06-20
It's usually easier to paste the output here (using [code] tags to preserve formatting than to attach 

See the part that says 'Input/Output Error'?
That can be real bad.
It sometimes means your hardware failure - the hard drive may be dying.

Search for how to run a SMART check on your drive to eliminate faulty hardware as a culprit.

---

### Post by este.el.paz on 2017-06-20
> **ian-weisser said:**
> It's usually easier to paste the output here (using [code] tags to preserve formatting than to attach 

See the part that says 'Input/Output Error'?
That can be real bad.
It sometimes means your hardware failure - the hard drive may be dying.

Search for how to run a SMART check on your drive to eliminate faulty hardware as a culprit.

@ian:

Alrighty, thanks for the thoughts; it was a fairly long 2-3 "pages" doc, so I figured better to attach it . . . but, OK, I/O error . . . "death of ye olde HD" . . . as far as things go, that wouldn't be the most expensive problem to fix . . . but, perhaps trying to find the part might be problematic?  

In the interim from when I posted this thread I was talking with a buddy about issues with iMacs and I remembered that when I set this machine down on the floor due to constant kernel panics, that I had had a shop do a diagnosis and they took a couple weeks to find "broken RAM" which we then replaced . . . only to have it "break" again after that . . . so I figured it was something "deeply internal" . . . and moved on.

I have SMARTReporter on the OSX side, but of course now it won't cleanly boot OSX . . . this morning I looked through the Xubuntu "systems" app and ran "cpu blowfish" . . . which didn't show any problems.  I didn't see anything mentioning SMART . . . but, sure, worth looking around for something to do that on the linux side.  I'll try the OSX Hardware Test in a bit, see if that will boot . . . not figuring it will.

I'll post back with any interesting developments or discoveries . . . .

e.e.p.

---

### Post by este.el.paz on 2017-06-20
Latest update:

Turns out I had gsmartcontrol installed in Xu, so I ran that after I ran two different Apple Hardware Test CDs . . . which usually isn't too helpful as everything "passed."  So running gsmartcontrol's "extended test"  . . . the "general health impressions" were that it "passed" as well, but the extended test completed at 30% with a "read failure" . . . LBA of first error -- 88016818 . . . .

It showed the "ATA error count" at 90 . . . life hours 8375  with "uncorrectable error in data"  . . . "5 sectors at LBA=0x05e7320d=99037933"

In one of the other tables it showed in "Attributes" . . . a number of boxes with **pre-failure** and others mostly with "old age" . . . .  Previously I think I saw these "pre-failure" stats and I optimistically viewed them as meaning, "before" or "yet to fail" and seeing that as a "good thing" . . . but, with time comes "pessimism" and the understanding that that probably means "imminent doom is about to happen, or is actually happening, and this is the last ray of light before all goes very, very dark . . . "  ???

So, I'll look around and see if HDs are still available for this machine . . . I'm not too worried about the OSX side, as I have a clone back-up that I could clone back into the system . . . but, I'm figuring that if I could transfer data for the Xubuntu side, it probably isn't recommended as some data has been damaged, and that would transfer into the new HD and wouldn't be any more repairable than it is now??  Still have the "special" Xubuntu 12.04 installer to do a fresh install if and when we get there . . . just have to refresh my memory on whether that needed boot params to run . . . .

Back when there is something else to report.

.e.p.

---

