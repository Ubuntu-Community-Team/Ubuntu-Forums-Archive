---
title: "A Couple questions before I Install"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by mrwonx on 2007-01-26
Hi all, Linux semi-noob here.

I've installed and run Ubuntu several times, testing it out, giving a friend an alternative OS, etc., but eventually went back to Windows to run my necessary programs. Vista is coming out, and as with many, it scares me to death. 

I've read and understand all the steps in the dual boot guide, and am now pretty dead set on doing the install over this weekend. 

Here are my questions:

1. I have a Maxtor Ultra ATA/133 PCI Adapter Card that runs my 2 biggest hard drives - both formatted to NTFS. The Bios see's this card. Will Ubuntu see this card off the install, or is there a driver I should be looking for?
1a. Will I need to re-format my NTFS into Fat32, or is there a work around?
2. I have a 64 bit processor. Aside from minor flash work arounds and program tricking, what is the plus to installing the 64 bit version? I have 1GB of Ram, will that be enough to run things quicker in 64bit?
3. Is there a stable "replacement" for DVD Shrink, or should I just install it through Wine?


Thanks in advance for the help. I tried searching both the forums and Google for my answers (aside from 3, but I figured since I was posting . . . ) and wasn't coming up with anything concrete.

---

### Post by citizenofnowhere on 2007-01-26
Hi!

I can't answer all of your questions for cetain, but I can try to tackle a few :)

1) A good guide to what hardware works with Ubuntu is the livecd - if it works on the Edgy livecd, odds are you're good.

1a) - whether you need to format depends on what you're going to do. If you're not going to write anything onto those partitions from Ubuntu, stick with NTFS. Though I suspect you will want to given the first question - there is an *exmerimental* package in Synaptic to allow writing to NTFS partitions - it's called ntfs-3g. Most testers found it works OK - to prevent errors when you boot into Windows later, download the "ntfprogs" package, and run ntfsfix from commandline. It's designed to fix anything the new driver might damage. What I did was use FAT32 for shared stuff, because even though it's less stable I didn't want the headache of the off-chance Windows didn't boot up on me. 

2) 1GB of ram is generally good enough for most things on Ubuntu. Not Vista though (I tried). I think the only thing you need to worry about is drivers. Not every application comes with a 64 bit version, and 32 bit versions can run a little laggier. I can't think of anything that doesn't come with a 32 bit version though, so it could be safer. Someone in another thread suggested a parallel install of both - I suggest using the livecd again. You won't be able to gauge speed but other than that you can take stuff for a spin.

That having been said, the other day I helped put a 32bit version on a fujitsu amd 64 lappie with no problems (because our 64 version crashed during installation - probably a bad download)

3) Run it with wine if you're familiar wth the interface. I've had many successful attempts (I now run Photoshop, a bunch of ISO tools, registry tools, a few 3D games with wine and love it). Here's a good site with different versions that have been tested out:

[http://appdb.winehq.org/appview.php?iAppId=1533](http://appdb.winehq.org/appview.php?iAppId=1533)

You might have to go with a slightly older version, but that's not always a bad thing. You can find old versions of software here:

[http://www.oldversion.com/](http://www.oldversion.com/)
[http://www.oldapps.com/](http://www.oldapps.com/)

Or just google for DVDShrink with whichever version you think should work based n the comments on appdb.

Have a good install!

[EDIT] Try dvdrip from Synaptic - I've used it with a fair amount of success and it has the widest range of options I've seen. It can be a little overwhelming on first try ebcause of everything you need to configure, but after you've done it once you'll be alright.

---

### Post by lyceum on 2007-01-26
1. It should "see" the NTFS, but files may be read-only (only guessing from experiance). Linux seems to see fat32 better.

2. Go with the 32 bit. More programs are supported.

3. Yes. All I can tell you about it though is you can get it from automatix getautomatix.com)

---

### Post by mrwonx on 2007-01-27
Thanks for the answers.

So far, I burnt all of my iso's I had lying around to free up space. I've formatted 2 of the 4 hard drives as Fat32 (Only my C Drive and the drive with all my remaining files remain unformatted), and I'm in the process of moving 200GB of files to the Fat32 drives so I can format the remaining HD.

Another question before I start installing - would it be beneficial to Dual Boot Windows XP if I have access to a WinXP machine less then 5 feet away? I think I've pretty much answered my own question, but is there any other benefit to Dual Booting that can't be solved in just a network share?

---

### Post by lyceum on 2007-01-27
> **mrwonx said:**
> Thanks for the answers.

So far, I burnt all of my iso's I had lying around to free up space. I've formatted 2 of the 4 hard drives as Fat32 (Only my C Drive and the drive with all my remaining files remain unformatted), and I'm in the process of moving 200GB of files to the Fat32 drives so I can format the remaining HD.

Another question before I start installing - would it be beneficial to Dual Boot Windows XP if I have access to a WinXP machine less then 5 feet away? I think I've pretty much answered my own question, but is there any other benefit to Dual Booting that can't be solved in just a network share?

I find no benefits to dual booting. If you really need XP check one of the how-to's on running XP inside windows or pick up a program like Win4Lin or Crossover Linux. My 2 cents.

---

