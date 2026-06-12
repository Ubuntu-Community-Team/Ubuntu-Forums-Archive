---
title: "MacBook Pro 2,1 - ACPI Issues"
date: 2012-12-24
forum: Apple Hardware Users
---

### Post by Benjamindaines on 2012-12-24
I'm running on an old school second generation MacBook Pro (2,1) and my battery meter doesn't seem to be working they way it should.  Every now and then it will report that I have 0 battery charge remaining. The battery condition is fine, I've only had it about a year, and the hardware button says I still have plenty of charge left.  If I call up acpi from a terminal window it will say no battery found.  Any ideas?

---

### Post by N00b-un-2 on 2012-12-24
That definitely sounds like a hardware issue.  I would suggest picking up a cheap MBP battery off amazon or ebay.  I know that some of the later generations of MacBooks had ACPI issues on Ubuntu.
You didn't mention which version of Ubuntu you are trying to run, nor which version of OSX your MBP has (to the best of my knowledge, 10.7.5 is the latest version your laptop supports due to only having 32 EFI despite being 64 bit capable).
Does battery status report properly on OSX?

---

### Post by Benjamindaines on 2012-12-24
> **N00b-un-2 said:**
> That definitely sounds like a hardware issue.  I would suggest picking up a cheap MBP battery off amazon or ebay.  I know that some of the later generations of MacBooks had ACPI issues on Ubuntu.
You didn't mention which version of Ubuntu you are trying to run, nor which version of OSX your MBP has (to the best of my knowledge, 10.7.5 is the latest version your laptop supports due to only having 32 EFI despite being 64 bit capable).
Does battery status report properly on OSX?

I might try picking up a different battery (or putting my old one in), but I don't really want to spend money on this machine, as it's my secondary computer and basically just an internet machine.  I nuked OS X from the hard drive, Ubuntu 12.10 is the only OS on here.  I also experienced this problem with Fedora 17, which makes me think it's either a hardware issue or something to do with ACPI itself that I need to tweak in order for it to like my hardware.  It definitely does it less in Ubuntu than Fedora.  I've never seen it happen in OS X when I had that running on here though.

---

### Post by N00b-un-2 on 2012-12-24
hmmm... if two "modern" linux distros are displaying the same behavior, but you are inclined to think that it may still be a software issue, it would be worth the time to grab an older, less bleeding edge distro (like maybe 10.04 LTS for example) and try it out on your laptop.  Despite their very best efforts over at kernel.org, occasional regressions do occur, since they can't always test EVERY single new kernel and module on EVERY piece of hardware and platform available.
I figure it's worth a shot before throwing a new battery at it, because Linux is free, but the hardware it runs on is not.

---

