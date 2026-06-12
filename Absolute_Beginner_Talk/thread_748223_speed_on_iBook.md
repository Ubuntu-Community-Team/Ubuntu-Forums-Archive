---
title: "speed on iBook"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by adamohern on 2008-04-07
Hi folks:

I'm getting too old for this stuff :) Reading these forums is intimidating!

I've got an old iBook (G3?) with DVD running OSX.4. It's gotten very slow, even though we recently did a clean install. I was wondering if there might be a linux OS option that would be snappier and give some new life to this old box. I think we could get by with open source office apps, as long as they're fast and easy to use.

So my question is this: what's the fastest OS I could install on this machine and still be able to do my gmail and web browsing? I'd also need to be able to run some kind of office suite. Would the performance increase be noticeable?

The second part of my question: is there any easy way I could "try it out" before erasing the current hard drive?

Thanks for your help!

Adam

---

### Post by jkeyes0 on 2008-04-07
If it's a G3 iBook, it should have the PowerPC processor, so you'll have to look for a version of linux that will run on PPC. I believe Ubuntu has stopped supporting PPC, but looking at [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/), it shows ubuntu-7.10-desktop-powerpc.iso as an option, so you might check that out (it's a LiveCD, so it'll give you the chance to test it before installing).

---

### Post by adamohern on 2008-04-07
Thanks, I'll give that a try.

---

### Post by MONODA on 2008-04-07
there is also yellow dog linux which is supposed to be the best ppc linux version.
[http://www.terrasoftsolutions.com/products/ydl/](http://www.terrasoftsolutions.com/products/ydl/)

---

### Post by scramasax on 2008-04-07
> **adamohern said:**
> I've got an old iBook (G3?) with DVD running OSX.4. It's gotten very slow, even though we recently did a clean install.

Shouldn't make any difference -- it's not like Windows where there's a Registry to get gummed up.  There shouldn't even be any problems with fragmentation over time.

If you'd installed an awful lot of software and/or had a lot of large files -- multimedia, say -- on there that wouldn't help. You don't really want to fill the hard disk on a computer more than about half full.  Otherwise, the solution is to buy more RAM -- those machines didn't tend to ship with very much and the later versions of the OS may be a little more demanding than the version a G3 would have come with.

>  I was wondering if there might be a linux OS option that would be snappier and give some new life to this old box. I think we could get by with open source office apps, as long as they're fast and easy to use.

Ubuntu *might* be a little faster on comparable hardware.  But, really, I suspect you need more RAM in there.

> So my question is this: what's the fastest OS I could install on this machine and still be able to do my gmail and web browsing?

Xubuntu, which uses a lightweight desktop environment would probably be somewhat quicker than either the standard Ubuntu 7.10 or OS X 10.4.  I don't think it's currently available in a version for the PPC processor, however -- can't see one here:

[http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/](http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/)

>  I'd also need to be able to run some kind of office suite. Would the performance increase be noticeable?

Yes, office suites can be quite demanding.  You'd want to be running Open Office if you're doing serious processing of office documents rather than, say, a little word-processing and no spreadsheets, etc.  Open Office  is not exactly lightweight.

> The second part of my question: is there any easy way I could "try it out" before erasing the current hard drive?

Yes -- all the current Ubuntu releases are both install CDs and "live CDs".  That means they will run off the CD:

[http://en.wikipedia.org/wiki/LiveCD](http://en.wikipedia.org/wiki/LiveCD)

I wouldn't, in any case, wipe the hard-drive even if you find what you try acceptable: it will, by default, install alongside OS X, and you'll be offered a choice of what to boot into at boot-up.  Machines running that processor weren't a big part of the market, and Apple itself no longer uses it.  This means that the PPC version of Ubuntu is not a high priority for Canonical, because few people are going to want it.  It may even be a purely "community project" rather than official version these days.  You might have trouble with certain things -- browsing the web at flash-enabled sites, for example.  better if you can swap between the OSes as a when you want to.

But try the live Ubuntu CD, and see if it does what you want.  In any case, I'd advise you to get more RAM for that machine -- it's reasonable enough in price from some 3rd party vendors who specialize in supplying it.

---

### Post by ZeSteves on 2008-04-08
carefull with the distro you choose! i have a powerbook g4 (PPC architecture)  and i had several issues with situations as mouse too slow, keys not working, etc.
If i'm not wrong the last os from ubuntu is 7.04 or 6.10 to ppc ( i got to double check) and it seems to run smoothly. Do not use fedora, so many issues with it (sorry fedora guys). be patient and read all the forums before making a decision. try the live cd from ubuntu and good luck.
don't forget the c button during boot up to access directly the cd:)

---

