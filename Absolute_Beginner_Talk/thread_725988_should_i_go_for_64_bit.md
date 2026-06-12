---
title: "should i go for 64 bit?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Funky91 on 2008-03-16
I know this is a bit nooby but...

I am thinking of building an ubuntu only pc. I will probably get a 64 bit cpu. Would it be possible to therefore run either 32 bit programmes in 64 bit ubuntu or to run 32 bit ubuntu on a 64 bit processor.

---

### Post by nonewmsgs on 2008-03-16
it used to be much harder to do things under x64 but that is no longer true.  it is still "easier" in some cases, but there are wizards now to do the more difficult things like installing flash.  with 64-bit you are taking advantage of your processing power and i highly recomend it.

---

### Post by Funky91 on 2008-03-16
can I still use 32 bit programmes because i hear that there are still alot of apps that are only available in 32 bit?

---

### Post by ghost_ryder35 on 2008-03-16
> **nonewmsgs said:**
> it used to be much harder to do things under x64 but that is no longer true.  it is still "easier" in some cases, but there are wizards now to do the more difficult things like installing flash.  with 64-bit you are taking advantage of your processing power and i highly recomend it.
agreed.  Everyday that goes by it gets easier and easierto be 64bit.

---

### Post by Sef on 2008-03-16
The only thing that does not have a 64-bit application is flash, but there are tools to help install the 32-bit version under a 64-bit system.

---

### Post by jan quark on 2008-03-16
check also carefully if there are 64 bit drivers for your hardware

I had bad luck because there is no 64 bit driver for my usb wlan fritz stick

---

### Post by abalone on 2008-03-16
What about WINE on a 64 bit Linux, will it still run 32 bit Windows apps?

What about 32 bit Windows VSTs? I can run them now from within a 32 bit WINE-run Windows sequencer but also via a native Linux tool "fst", compiled from scratch 

What about Windows codecs?

---

### Post by nonewmsgs on 2008-03-16
> **abalone said:**
> What about WINE on a 64 bit Linux, will it still run 32 bit Windows apps?

What about 32 bit Windows VSTs? I can run them now from within a 32 bit WINE-run Windows sequencer but also via a native Linux tool "fst", compiled from scratch 

What about Windows codecs?

wine only runs 32bit windows programs and will work fine for you.  the nonfree codecs work fine in 64bit.:popcorn:

---

### Post by abalone on 2008-03-16
> **nonewmsgs said:**
> wine only runs 32bit windows programs and will work fine for you.  the nonfree codecs work fine in 64bit.:popcorn:

Cool. Though to be honest I was secretly hoping somebody would say "nothing will work! Stick with 32 bit!" because now I'll feel an urge to switch and that'll probably entail some rebuilding-from-scratch (though, uhm, wait, would something I compiled on 32 bit Ubuntu still work or not...)

How much of a performance benefit is it anyway? Right now, everything seems fast enough. It's those old harddisks I seem to be waiting for the most.

---

### Post by abalone on 2008-03-24
Ok, I did it... 64 bit Gutsy. Went very smoothly. I don't think I can notice the difference, except: none of the rather specialised tools I had to compile from source are still compile-able, or if they are, they crash. Nor do the READMEs help, or any tricks I found online. I think I'll go back to 32 bit, kinda depressing when you're using WINE half the time because you can't run your Linux apps on ...Linux. Maybe in another few year. Wish I'd known this in advance...  :confused:

---

### Post by linuxgrrl on 2008-03-24
this may be too late for you, but there is a tool called "getlibs" which helps install the needed 32 bit libraries when trying to compile programs on 64 bit (I'm probably saying that wrong, but you get the idea).  

Before you rebuild again, you might try getlibs and see if it can make your special apps compile.  I have not tried it but people seem to like it a lot.

---

### Post by abalone on 2008-03-24
I had tried getlibs, actually, but it either didn't accomplish much or not enough or not the right things, or (very, very likely:) I didn't know what exactly to do with it...

Got comprehensive help from the developers of two of the apps in question (within an hour of asking, even); as for the rest... I'm not sure. 

Now how do I make Pidgin, Konqueror, Kmail etc. use 32 bit "Swiftweasel" to open http links?...

---

### Post by cotcot on 2008-03-24
Install both versions as dual boot. Measure the speed advantage of the 64 bit for your application and decide than or use 64 bit for those apps where you see a significant speed benefit.

---

### Post by abalone on 2008-04-04
> **abalone said:**
> I had tried getlibs, actually, but it either didn't accomplish much or not enough or not the right things, or (very, very likely:) I didn't know what exactly to do with it...

Got comprehensive help from the developers of two of the apps in question (within an hour of asking, even); as for the rest... I'm not sure. 

Now how do I make Pidgin, Konqueror, Kmail etc. use 32 bit "Swiftweasel" to open http links?...

Never mind. It's not Ubuntu's fault (and I really like Ubuntu in general) if third-party source code isn't 64-bit-ready or if browser plugins don't work properly - but I'm better off using the 32 bit Ubuntu for the time being (or another distro, considering the -rt kernel doesn't work either.)

---

