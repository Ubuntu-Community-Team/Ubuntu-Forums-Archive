---
title: "Adobe Flash player..."
date: 2007-09-28
forum: Apple PPC Users
---

### Post by IanGodfrey on 2007-09-28
Is there anything that will do the job on the PPC mac platform?  All this other information is all well and good, but PPC is a different story.

---

### Post by 3rdalbum on 2007-09-28
You could try installing Gnash - it's in the repositories in the recent versions of Ubuntu, and it's not impossible to install from source code if necessary.

---

### Post by jrib on 2007-09-28
I use nspluginwrapper on 64bit.  I don't have any ppc boxes, but it may be worth a try: [http://gwenole.beauchesne.info/en/projects/nspluginwrapper/help](http://gwenole.beauchesne.info/en/projects/nspluginwrapper/help) .  That page seems to mention it, so it seems possible, but you will need to do some more research.

---

### Post by Doctor J. on 2007-09-28
> **3rdalbum said:**
> You could try installing Gnash - it's in the repositories in the recent versions of Ubuntu, and it's not impossible to install from source code if necessary.

I have Gnash installed [following the instructions on the PowerPC FAQ: [https://wiki.ubuntu.com/PowerPCFAQ#head-7e0d9b980507337bf9c80768cabb8396a552335c](https://wiki.ubuntu.com/PowerPCFAQ#head-7e0d9b980507337bf9c80768cabb8396a552335c) ].  However, by default the Gnash package does not include the plugin 'mozilla-plugin-gnash'.  You'll have to install that separately - it can be installed via Synaptic if you have added repositories [I believe it'll be in the 'medibuntu' repo].  

Also keep in mind that Gnash is fully compatible with Flash V7 and partly compatible with Flash V8, but many commercial sites have fallen into the trap of using "latest and greatest" Flash V9.  This is only available to us on the x86 cpu.  I don't know why they would want to deliberately make their site unviewable to so many browsers, but there it is.:popcorn:

---

### Post by dynamicv on 2007-09-28
> **Doctor J. said:**
> Also keep in mind that Gnash is fully compatible with Flash V7 and partly compatible with Flash V8, but many commercial sites have fallen into the trap of using "latest and greatest" Flash V9.  This is only available to us on the x86 cpu.  I don't know why they would want to deliberately make their site unviewable to so many browsers, but there it is.:popcorn:
Personally I wonder whether the relationship between Adobe and Apple has anything to do with it.  Apple probably aren't too keen on their PowerPC users moving over to Linux and keeping the same hardware.

---

### Post by Doctor J. on 2007-09-28
> **dynamicv said:**
> Personally I wonder whether the relationship between Adobe and Apple has anything to do with it.  Apple probably aren't too keen on their PowerPC users moving over to Linux and keeping the same hardware.

Um, if that were the case, i'd think that the OS X plugin would only work for Safari rather than also the other browsers.  I assume it's more the usual lack of respect commercial developers have for linux.  Note that even the x86 users can only get Flash V9, while Shockwave is completely unavailable within Linux.

---

