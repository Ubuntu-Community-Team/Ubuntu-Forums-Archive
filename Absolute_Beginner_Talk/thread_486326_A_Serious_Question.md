---
title: "A Serious Question"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-06-27
Along with the Live CD, there is a program called memtest, right? Well, I ran it, and it did two passes, and came up with 13 errors. What exactly does that mean?

---

### Post by ramjet_1953 on 2007-06-27
What exactly was the reported error?

Generally, if you are getting errors, you may be having a problem with the RAM that you have installed, or the associated controller.
If this is the case, you may get random crashes and lockups.

Regards,
Roger :cool:

---

### Post by DBStevens on 2007-06-27
Well systems that present memory errors are unstable.

Basicly you have memory on your machine that is bad or going bad and that can lead to really strange things happening.

Things like currupted files, programs that crash, don't run, or produce incorrect results, inconsistent events can occur.  In short you are headed for trouble at some point or it has happend and you haven't found it yet.

Can you take a picture of the errors memtest has found and post it somewhere and provide a link to it.

---

### Post by tcoffeep on 2007-06-27
How do you take a pic of it?

---

### Post by crav on 2007-06-27
This might seem stupidly obvious, but a digital camera is probably gonna be your easiest option.

---

### Post by tcoffeep on 2007-06-27
I don't own one.

I just have this laptop, and thats all.

---

### Post by DBStevens on 2007-06-27
It isn't critical to see that picture.  It is important to have a system that doesn't have memory errors.  

I'd have a hardware person run their dianostics on the computer and take it from there.

---

### Post by tcoffeep on 2007-06-28
How do you connect Ubuntu to a digital camera? [a friend came by with one]

---

### Post by Webby_s on 2007-06-28
Bring it up to your eyes and then look through the viewer on the camera... snap a pic .... download it to your desktop and post it on your post in this thread.   Well as far as I know. That is my two cents ...someone else may have a better idea. But I think it will work! Good luck and report back!

---

### Post by Bartender on 2007-06-28
Ubuntu should see the camera as a USB device, placing an icon on the desktop.  If it has a USB output cable, try plugging it in, follow the same steps you'd use for a Windows PC (with my Olympus SP-500UZ a little menu pops up and I hit the "PC" option).

However, this may not be that important if you can't make it happen.  We're talking about a laptop, right?  Open up the little hatch covering the SODIMM module(s).  If you're lucky there will be two SODIMM's.  Figure out the #1 slot.  Pull the SODIMM out of the #2 slot and run memtest again.  If you get no errors, swap the SODIMM's and run it again.  Chances are only one of the modules is showing errors.  That way you could at least run the thing with the one memory stick while you decide what to do.

If the laptop doesn't run memory in dual-channel mode you could just replace the bad piece with something similar.  If your lappy does run memory in dual-channel mode you'll probly just want to replace them both.  It's hard to find identical modules, and if you plug in a replacement module with different timing than the existing one you'll just trade one problem for another.

---

### Post by tcoffeep on 2007-06-28
Well, I have an Acer Aspire 5100 series, and I can't seem to find the hatch covering the modules. Is there some site that might help with this little predicament?

---

### Post by Bartender on 2007-06-28
I googled the Acer manual
[http://www.acerpanam.com/synapse/data/7117/documents/AS5110_5100_3100-ENG-OLM_0425.pdf](http://www.acerpanam.com/synapse/data/7117/documents/AS5110_5100_3100-ENG-OLM_0425.pdf)

Page 33 shows a picture of the bottom.  Hopefully I was able to attach the jpg.  The area labeled as #2 is supposed to cover the memory modules.  I can't tell for sure but it looks like a large hatch, not a small one.

Found this discussion
[http://forum.notebookreview.com/showthread.php?p=1926273](http://forum.notebookreview.com/showthread.php?p=1926273)

---

