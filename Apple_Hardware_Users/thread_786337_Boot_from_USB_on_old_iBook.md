---
title: "Boot from USB on old iBook?"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by Shampyon on 2008-05-08
I've not much experience with the Mac. The last time I used one was in the eighth grade, some 14 years ago. A work supervisor heard that I wanted to have a small Linux notebook to hook up to my USB sound card and sound mixer for a portable audio recording setup, and donated an iBook to my cause.

Being a Mac newb I can't tell what version iBook this is. All I know is that it came with OS9. One of the provisions of the donation was that I remove the hard drive and return it to my supervisor for use as a 6GB portable drive. That's fine by me, as I always planned to have the notebook OS boot from USB.

My questions are thus:

1) How do I, if it is indeed possible, go about installing Ubuntu to a 4GB USB flash drive and have it bootable from my iBook?

2) Since this will be primarily used for audio recording and editing on a limited drive space, which version of Ubuntu would be best for the task?

---

### Post by stream303 on 2008-05-08
Let's find your model of iBook here:
[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

If you upgrade the hard drive on a very early model, be aware that unless you upgrade the firmware, you may be limited to keeping Ubuntu inside the 8gb partition limitation, ideally 7gb to play it safe on the replacement hard drive.  Since you have an original 6gb drive, this firmware limitation is likely, unless the former owner upgraded firmware already.  Since you have OS9 running already on a hard drive, it is a good candidate for a firmware upgrade (of course, determine your own risk-level / need to do this - firmware upgrades always make me nervous..)

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

Try to find out exactly what you have, and how much ram is installed, and you'll be better able to know if audio editing / recording on that box would be practical, or a slow annoyance. :)

---

### Post by Shampyon on 2008-05-08
It's definitely one of the two iBooks G3/500 Dual USB. I'm pretty sure it's the [first]("http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html") of the two. It has the standard 128mb RAM with an extra 64 stick. Bmb VRAM on the ATI video.

---

### Post by stream303 on 2008-05-08
Great - although if your primary objective is to run audio apps on it, I'm not sure how well it would run in the long term - maybe some audio guys could pop in..

Stmiller, where are you?  Long time, no hear! :)

Could you change the donation specifications to be just to get familiar with Ubuntu on ppc overall, in case the intended applications don't pan out from a practical standpoint?  I'd hate to see you tear into the machine and make the donor cry.. :)

---

### Post by Shampyon on 2008-05-08
It's okay, the machine was gonna get tossed by the company. It doesn't fit into their guidelines for passing on to end users - our group deals solely in refurbishing workstation PCs for lower income groups and individuals for work and school use. Our guidelines are such that we have to assume that the end user is the type that routinely confuses "Windows" for "That typing program." Definitely not the Apple crowd. 

Technically we're supposed to be scrapping the whole machine, but my supervisor and I are sneakily salvaging it for various purposes the company refuses to fund. Our section already had to tear apart another iBook and scrap everything but the RAM and HDD. So long as my supervisor gets a working hard drive at the end, he's happy. So long as I don't let anyone at work know the rest of the machine is in my home rather than in tiny pieces at the bottom of our industrial waste bin, I've still got a job :P

---

### Post by stream303 on 2008-05-08
Nice job - but don't sacrifice it for an old ibook... onwards...

The good news is that there is no official firmware update for the dual usb listed at the apple firmware page.

Now you can give the hd back, but what will you boot with?  Now I see the reason behind your usb-boot quest.  I'm not sure if this model supports it - although I think I've seen a few success stories....no personal experience with it.

With only 128mb you are pretty much limited to using the "alternative" non-live installer.  I'm not sure if the "live desktop" cd would work, although now that I think about it, I seem to remember articles about using usb-flash drives as swap to get live-cd's to boot and run with minimal memory machines - I'll have to look that up.

Are you intending to eventually replace the internal drive, or will you use an external firewire drive?  Not sure if the ibook will work without a drive in the first place...anyone tried that?

Your hardware situation raises some interesting questions I'll have to think about -- just be prepared that this probably won't be a drop-in installation. :)

---

