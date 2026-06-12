---
title: "Wanna scanna"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2008-02-19
Hi community !

When I started with Ubuntu back in 2006, I was quite surprised to find that my HP scanjet 4470c scanner was not plug-&-play as it had been for ages in Windows. (I seem to remember the Ubuntu slogan: “It just works…”).

Gradually, I realized that things were in fact far worse than that, and that no amount of patience or expertise was EVER going to see this scanner work under Ubuntu!

Still, I thought, it’s a pretty old scanner, so I can dual-boot with XP until it expires & then get one which is Linux-compatible.

Well – that time has now come, so I read all the reviews & short-listed some potential photo-scanners & checked to make sure they were all Linux-compatible...

What a disaster!
None of them can be used with Ubuntu!
At a glance, no scanner which appears respectably in any recent independent review can be used with Ubuntu!
OK – surely that must be wrong, but it’s my impression at the moment.

I would have chosen a Canon CS4400F or Epson Perfection V200 or maybe spent a lot more on an HP Scanjet G4050 or even an Epson Perfection V500 or a few other models in between, but as far as I can see, none of these work at all with Ubuntu.

I tried to wade through the lists of “Supported devices” & “Sane” (misnomer of all time) & “Genesys” etc etc but this feels like bursting into an un-maintained museum.
There are so many long-neglected trails of once-maybe-compatible hardware, but no clear simple list of “This will work, even for newbies”.
Or I have not found it.

Will latest & greatest Ubuntu 7.10 properly run any recent, decent, popular, affordable, findable photo-scanner with slide adapter?
If so – which one(s)?

Do we need to organise some kind of mass protest to get Canon, Epson, HP etc to wake up?
Or will the answer come from inside the Linux/Ubuntu communities?
Or do I just have to keep XP for ever?

---

### Post by ibizatunes on 2008-02-19
I found that 7.10, was fine running my epson 3450 scanner..... plug and play....
i think usb scanner support has improved alot....
[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)

---

### Post by 2CV67 on 2008-02-19
Thanks for the reply, ibizatunes.

The scanner you mention is not in the list you attach...

How would anybody know whether it might work or not before buying one?
I don't intend to buy another without reasonable assurance it should work.

My method had been to Google the scanner & Ubuntu & look for threads.
This told me CS4400F doesn't work at all & V200 may work in very limited fashion.

---

### Post by ibizatunes on 2008-02-19
Do u have a scanner now? Y dont you use that one, and test it on a live CD?

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)
Does my scanner work with Ubuntu?
There are three ways to see if you scanner works in Ubuntu: 

Simply plug it in and try it! If it is a newer USB scanner, it is likely that it will just work. 

Check  [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners) which is Ubuntu specific. 

 SANE project listing of support scanners - The SANE (Scanner Access Now Easy) project provides most of the backends to the scanning software on Ubuntu.

---

### Post by ibizatunes on 2008-02-19
Pick a model, then google it to see if many people have problems, with that scanner,

---

### Post by aeiah on 2008-02-19
i have an HP printer/scanner that 'just works' with ubuntu 7.10. granted, its pretty **** and only cost me £30, but try HP. id be suprised if their good ones dont work if they can be bothered to make drivers for the crap ones.

---

### Post by 2CV67 on 2008-02-19
As I said in my initial post, I currently have an HP 4470c scanner which does not work in Ubuntu.

This thread covered that point from 2006 thru 2008:
[http://ubuntuforums.org/showthread.php?t=324714](http://ubuntuforums.org/showthread.php?t=324714)

Now I am ready to replace that scanner, so I want to buy a new one which works properly in Ubuntu.
I want to get one which will handle slides via a transparency adapter.

Naturally enough, I would like to buy a recent, decent scanner that I can find, today, in all the usual places where you buy scanners & at a reasonable price.

All those places are currently selling Canon CS4400F and Epson V200 & V500 and HPG4050 etc.

Obviously I don’t want to buy a new scanner then find it does not work, or only works badly, in Ubuntu.

So what I am looking for, is a list of new, current, available, photo scanners which will work properly in Ubuntu.

I keep looking at the lists of supported hardware & the lists of scanners on sale today, but they don’t match.

---

### Post by dryder on 2008-02-21
i have been posting about exactly the same problem - flatbed photo quality  scanner support is appalling in linux (& ubuntu?) and needs some serious attention for **current models**.

My Microtek E6 SCSI is supposed to work perfectly but is not recognised - no help why. Uses Adaptec AHA 2940 SCSI card which is seen by the system but not the device attached to it. XP has no problem.

My more recent Microtek USB Scanmaker 5800 is not supported, though it works OK in Virtual Box (just a bit slow, presumably as it clears the buffers). But I can not scan in linux - a pain.

The Epson Perfection V200 and V350 are supposed to work "requires DFSG non-free iscan-plugin-gt-f700<br>overseas version of the GT-F700" and the "epkowa" backend however one does that as a non technical person. The compatibilty is 'good', meaning "the device is usable for day-to-day work. Some rather exotic features may be missing". There is no explanation what that means nor do Epson know.

The whole scanner side of linux / Ubuntu is very frustrating and I am not prepared, just as others are not, to buy and hope.

Unfortunately it is the only thing stopping me turning off XP and the pain of booting to Windows just to scan is very annoying.

However it is acheived, more attention needs paying to PnP current scanners. "It just works" is not really true - yet...

That's my two bob's worth
David

---

### Post by Drakkenfyre on 2008-02-23
Yeah, I actually think that was a really bad decision by the Ubuntu folks to have that "it just works" line. Because, well, we're here.

I have found some current scanners on the Sane Project website. However, I see mention here of it being outdated. Is there any problem with using scanners that are listed as "good" or "complete" on that site? Or is it just that they're missing models?

Thanks!

---

### Post by Drakkenfyre on 2008-02-29
Bump. Is the Sane Project website a reliable source? Thanks.

---

### Post by Dr Small on 2008-02-29
> **Drakkenfyre said:**
> Bump. Is the Sane Project website a reliable source? Thanks.
Yes, and there is a fellow in my LUG who writes drivers for Sane.

---

### Post by momist on 2008-03-21
Hi 2CV67,

This may not help much, but I'm using a very old Epson GT-7000 on a scsi pci card that "works out of the box".  This has a photo facility with overhead lamp device for trannies.  The downside is that I've not yet found out how to make it work unless it is already switched on at boot time, but I'm sure I'll figure that out when it bugs me enough.

The point I am trying to make is that in plain Ubuntu 7.10 scanner support has improved very much over all previous releases, and I've now managed to ditch Windows for good!  Much good!  :)

I would suggest you follow up on the post that suggested you choose a modern scanner to your liking, and then Google for problems/Ubuntu users comments.

---

### Post by 2CV67 on 2008-03-21
Yes - I bought an Epson Perfection V200 yesterday....

This after reading a thread which suggests it should work to some extent:
[http://ubuntuforums.org/showthread.php?t=627650](http://ubuntuforums.org/showthread.php?t=627650)

Today I am playing with it in XP & will try it in Ubuntu soon.

Fingers crossed!

---

### Post by jel0327 on 2008-04-29
I had the same problem with my scanjet 4470c.  In early 2008 I found that libsane-extra has the needed drivers to work with the scanjet 4470c and some others.  Ubuntu has it in its package manager.

[http://packages.ubuntu.com/feisty/libs/libsane-extras](http://packages.ubuntu.com/feisty/libs/libsane-extras)

James

---

