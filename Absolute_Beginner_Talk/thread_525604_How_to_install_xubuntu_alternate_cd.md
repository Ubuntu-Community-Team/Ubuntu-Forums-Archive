---
title: "How to install xubuntu alternate cd?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zachboy82 on 2007-08-14
Hello! 

  I'm sure this has been asked before but i could not find it on the forums so here goes...  I have an old compaq armada 1592dmt laptop with 65 megs of ram.  I'm installing xubuntu alternate on it but heres the kicker... the laptop does not have the option to boot from cd rom drive.:mad:  I've tried several things but nothing works.  I tried removing the laptop hdd and hooking it up to my regular computer and installing xubuntu.  This worked somewhat but xubuntu was configuring for the video card on my desktop and not for the laptop so xserver would not work properly.:(

  My next idea is to use mini linux on a floppy to boot the laptop, and then tell the laptop to access the cd rom drive and do an install directly on the laptop.  will this work?  if so, how do I go about telling the laptop to boot the cd?  as I stated before the bios has no option for booting from cd.  What other options are there?  Any help is very much appreciated! :)

I dont have internet at home so Im trying to get this laptop working with a wireless pcm/cia card for wi-fi.  then I get internet for free!!  :lolflag:

anyways, thanks in advance!

zachboy

---

### Post by ThinkBuntu on 2007-08-14
Psst....*Debian Floppy Netinstall*...

---

### Post by wolfen69 on 2007-08-14
64mb of ram wont work. ive tried it. you need at least 128. if you did manage to get it to load, it would be so slow it wouldnt be worth it. try damn small linux, or puppy linux.

---

### Post by zachboy82 on 2007-08-14
> **ThinkBuntu said:**
> Psst....*Debian Floppy Netinstall*...

doesn't netinstall require internet access?  eh I'll do more research before I ask questions.



[wolfen69: 64mb of ram wont work. ive tried it. you need at least 128. if you did manage to get it to load, it would be so slow it wouldnt be worth it. try damn small linux, or puppy linux.]

With the alt cd it says it works with 65 megs of ram.  Is this incorrect?

thanks again!

zachboy

---

### Post by bulldog on 2007-08-14
It could be you manage to install after a loooong time:)
I did an install on a computer with 192MB of RAM,believe me,it takes forever.
But it's possible I suppose.

Puppy Linux is a fair alternative,just take a look at it.............

---

### Post by eldepeche on 2007-08-14
I think Smart Boot Manager will work. It's a floppy bootloader that searches for any bootable hard drives or CDs and gives you a menu to choose one.

---

### Post by ThinkBuntu on 2007-08-14
Oops, I didn't read the last part where you mentioned that you're without internet access. I'd suggest any of a variety of available teeny-tiny, low-resource distributions for an easy setup - Damn Small Linux is one such distro. There are a few others, but I can't remember their names.

Debian and Slackware both have good ways to boot and install a system from floppies only, with no internet connection. I think that it would be a good idea for you to look into these, because you'll end up with more choice over how your final system is. I think that OpenBox or FluxBox would work great for such a low-resource environment. If you attempt a more custom install using Debian or Slackware floppies, then you should research ahead of time as to what sort of software mini distributions are using (like DSL).

---

### Post by zachboy82 on 2007-08-14
sweet!  thanks for the replies!  I'm actually leaning towards puppylinux.  I do have a question though, would ndiswrapper work with puppy?  I need it for my wireless card to work.  Oh good it just finished downloading.  I hope this works...

thanks guys!

zach

---

### Post by ugm6hr on 2007-08-14
> **zachboy82 said:**
> I do have a question though, would ndiswrapper work with puppy?

Yes.

In fact, as of v2.14, Puppy has ndiswrapper built-in, with an easy GUI to get it working with minimal effort.  So, in fact, it is easier than (X)ubuntu in this sense.  Just look for network or internet or something like that in the menu.

---

### Post by bwtranch on 2007-08-14
Ditto. Use puppy. You have to have 512 M nowadays and a gig is better.

---

### Post by zachboy82 on 2007-08-14
> **bwtranch said:**
> Ditto. Use puppy. You have to have 512 M nowadays and a gig is better.



wait...what?  I only have 64 megs of ram on my laptop.  I thought you could run puppy on 32 megs??  now Im upset.

zachboy

---

### Post by ugm6hr on 2007-08-14
> **zachboy82 said:**
> wait...what?  I only have 64 megs of ram on my laptop.  I thought you could run puppy on 32 megs?? 

Puppy will work fine on 64MB RAM, as long as you have a swap partition available.  You will be able to use the LiveCD, but it may be unbearably slow.

My suggestion - boot Puppy (or DSL, if you have it) and create a 128MB swap partition (you can use command cfdisk)

Then reboot Puppy again, and then install.  It'll work just fine - I have done this (albeit with v2.14) with 64MB RAM.

---

### Post by zachboy82 on 2007-08-15
alright!!  I'm accessing the internet with my very old compaq now on puppylinux with a dynex (best buy brand) wireless card.  It took a few tries to figure out what to do but it was EASY once I figured it out!  I just want to say thank you all very much for helping me out.  The easiest way to get my laptop to install the system was to get "boot manager" onto a floppy and then boot from cd rom drive.  Once I did that, I formatted and installed puppy onto my laptop.  Worked like a charm.  It is a tad slow but thats ok, all I'm using it for is internet.  Free internet!!!  I love wi-fi.  

Oh yeah, the dynex card works great... All I had to do with puppy was go to network manager and it detected that I had an uninstalled device.  I put the drivers for the card onto a flash drive, mounted the drive, then used ndiswrapper to install it.  Easy peasy.

Anyways, long story short, thanks a lot for the replies and the very helpful information!  I am now one happy camper.

zachboy:guitar:

---

### Post by ugm6hr on 2007-08-15
If SeaMonkey is too slow - consider using Opera.  It's what I used for my 64MB install with Puppy, and is a fair bit faster.  Unfortunately, Opera in Puppy only supports Flash7 (not 9) - look on the Puppy forum for advice regarding this.

---

