---
title: "MacPro Tower - NOT MacBook or MBP - + Ubuntu 14 Trusty"
date: 2015-09-20
forum: Apple Hardware Users
---

### Post by imattux on 2015-09-20
Before I get started, I want to see if there's anyone else out there running **Trusty** (or at least Precise) on a **MacPro Tower**. Mine is a 1,1. (looks kinda like a cheese grater) from **late 2006**. I had a hell of a time getting Ubuntu installed, configured and stable, but I've learned a lot that I'm happy to share with anyone who might be struggling. 

I've got 4 internal drive bays and at the moment, I've got Ubuntu 14 all by itself on one drive (for experiments, kernel testing, etc.), OS X (10.7.5) Lion all by itself on another, and the third has both Ubu and Lion. I'm not using Refit or Refind (although Rod Smith is a saint in my book and I'm forever grateful for his hard work, knowledge and generosity). I hold the alt/option key on startup and select which drive/partition to boot from.

So, if anyone has a similar setup or wants to experiment with a similar setup, we should compare notes.

Here are some things I want to explore:
1. I'm gonna buy a new **video card** so I can upgrade to Yosemite on the Mac side of things. I'd like to find a card that is **well supported on the Ubuntu** side. As of now, I'm unable to use the ATI drivers and I have to pass "nomodeset" to my kernel to get any video at all. I'd hate to spend $200-300 and end up still using the open-source Radeon drivers. If you don't have the same box as I have, I'm not sure that you can help, but maybe so. 

2. Getting my **sensors and fans** properly configured. Right now, I'm using macfactld and it runs around 2000-2500 all the time and it "sticks" when I switch to running OS X. This is a "better safe than sorry" approach and I'm ok with it for the time being, but for the longer run, I'd like to have a box that isn't blowing when it doesn't have to be.

3. **Compiling a kernel** that is as lean and optimized for this hardware as it can be. It will be less important when I upgrade the processors, but I'd like to be optimized in any case.

4. The biggest thing preventing me from running Ubuntu as my primary, daily OS is the fact that it **doesn't** **sleep**, turn off the monitor or even run a screen saver. Running OS X, the box goes to sleep after 15 min and is right back where I was ~15 seconds after I touch the keyboard or mouse. Not being able to do that will be a deal-breaker as far as Ubu being primary. Again, I think this is very hardware specific, but if you've got suspend working on your MacBook/Pro, lmk what works for you.

I'll leave things like that and see it I get any response. I hope so...

---

### Post by este.el.paz on 2015-09-21
> 4. The biggest thing preventing me from running Ubuntu as my primary, daily OS is the fact that it **doesn't** **sleep**,  turn off the monitor or even run a screen saver. Running OS X, the box  goes to sleep after 15 min and is right back where I was ~15 seconds  after I touch the keyboard or mouse. Not being able to do that will be a  deal-breaker as far as Ubu being primary. Again, I think this is very  hardware specific, but if you've got suspend working on your  MacBook/Pro, lmk what works for you.

@imattux:

I'm with you on the sometimes not having "suspend" in linux (what they call "sleep") . . . .  Sometimes suggestions have been made that the swap needs to be larger . . . like 2x RAM . . . but it could be in the kernel.  In my PPC units one running 12.o4 & the other 14.04 . . . they don't do "suspend" and that does relegate them to "second system" to the OSX side.  In my MBPro running triple boot OSXs & LM 17.1 Rebecca . . . I have "suspend" function.

e.e.p.

---

### Post by imattux on 2015-09-24
WRT 2. Controlling fans: I'm currently testing the solution I found here: [http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431)

So far so good, I'm tweaking the numbers as I write this. Core Temp avg. = 58*C and fan is @1200rpm...
[URL="http://ubuntuforums.org/showthread.php?t=1754431"]
[/URL]

---

