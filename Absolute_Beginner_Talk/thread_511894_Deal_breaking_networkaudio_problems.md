---
title: "Deal breaking network/audio problems"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by istara on 2007-07-28
System Specs:

Gigabyte 7VRXP Motherboard (Socket A)
- Onboard Ethernet Adapter: Realtek RTL-8139/8139C/8139C+
- Onboard Sound:  Creative CT5880
AMD Athlon XP 2000+
512 MB Corsair RAM
BFG Nvidia 6600 GT (AGP)

The Setup:
There is one router and two computers with wired connections.  One runs Ubuntu flawlessly, the other is switching from Windows XP.  Everything works fine in Windows.  All issues are identical on the hard drive as on the LiveCD.

Sound Issues:  
If I leave the onboard sound enabled, X doesn't seem to load properly (brown screen and eventually the unusable, all-white terminal appearing in the upper left).  The intro sounds stutter and go into broken-record mode although the mouse remains active and I can ctrl-alt-F1 and back again just fine.  Same results in recovery mode.  If I disable onboard sound, Ubuntu loads just fine, but I would really like to be able to use my sound card.

Network Issues:
DHCP will not return an IP address.  Setting a static IP has no effect.  I cannot ping the router, or anything else for that matter.  Packets go out, but nothing ever comes back.  Disconnecting the other PC has no effect.  Using the other computer's wireless Ethernet card or a wireless USB also return similar results.  Each card is detected and the right drivers are in place, but to no effect -- I still can't connect.

Conclusion:
???

I'm starting to think that perhaps my motherboard is just not compatible.  It has come to my attention that it is not listed as supported on the wiki (no Socket A Gigabytes are), but there's also evidence on these boards that some people have used it successfully.  I know the network card is supported and should "just work" but perhaps it is gigabyte's implementation that is messing things up.  If any gurus out there know of *anything* else I can try before giving up and going back to windows until I can afford a complete overhaul of core components, **please** let me know!

:( -istara

---

### Post by Pragmatist on 2007-07-28
What happens if you try a LiveCD?  You can use Ubuntu's LiveCD, but I prefer Knoppix.  One reason the LiveCD is useful for diagnosing hardware problems is that the LiveCD needs to be capable of working with more hardware out-of-the-box, since the user can't really modify the LiveCD.

---

### Post by istara on 2007-07-28
Ubuntu's live cd has all of the same symptoms both with the sound and the network.  I haven't tried Knoppix, but I could give it a shot.

---

### Post by istara on 2007-07-28
Knoppix results:

The audio reacts in the same way: constantly looping the first ~1.5 seconds of any sound, although it did not stop the interface from loading like it did in Ubuntu.

The networking reacts the same as well and cannot obtain an IP address (DHCP) from the router.

Is there something in my specs that is inherently anti-linux?

---

### Post by ReaderRat on 2007-07-28
Have you tried ```
aplay -l
``` to see if your sound card is recognized?
The "l" is a lower case "L".

---

### Post by istara on 2007-07-29
aplay -l:  both Knoppix and Ubuntu seem to recognize the sound card (when enabled) and comes up with an "Ensoniq" driver.  I'm not sure now to verify that that's the driver it should be using.

Being completely new, what's the easiest way to be copying and pasting these results since I have to switch to windows to access the forums?

---

### Post by Pragmatist on 2007-07-29
> **istara said:**
> ....what's the easiest way to be copying and pasting these results since I have to switch to windows to access the forums?

I would paste into a text file and transfer with a floppy.  You could also use a rewritable CD or DVD, thumbdrive, external hard drive, PDA, media card, etc...etc...

You could also manually write it down.  Possibly you could ssh from windows to your linux box, but you would have to install sshd onto your linux box and, since you can't connect to the internet, you would need to install sshd from a CD (unless the LiveCD has it installed).  Anyway, this last option can be confusing if you don't know what your doing.

Since they are small text files, I personally would just use a floppy (even though I have most of the media devices listed above).

---

### Post by armandh on 2007-07-29
different distros different drivers in the live cd
slaks would drive the sound on one so old it has an extra ide connection for your new ide cd. 
is the on board lan a 10/100 or just a 10 might be easier and better to disable and put in a new one

---

### Post by xpod on 2007-07-29
Well it cant be purely because it`s a Gigabyte socket A  i doubt as i have a similar seeming Gigabyte 7VKLMS Athlon XP2200(socket A) although i have the realtek audio to go with the same realtek network card you have and it all works out the box ....so to speak:)

Not sure if knowing that helps you any??

---

### Post by istara on 2007-07-29
> **xpod said:**
> Well it cant be purely because it`s a Gigabyte socket A  i doubt as i have a similar seeming Gigabyte 7VKLMS Athlon XP2200(socket A) although i have the realtek audio to go with the same realtek network card you have and it all works out the box ....so to speak:)

Not sure if knowing that helps you any??

Knowing that is at least encouraging.. maybe there is *some* hope for my current set up, but then I also seem to be running low on things to try.

Pragmatist:  Thanks for the tips.. I'm moving this weekend, but hopefully I'll be able to dig up my pen drive or a floppy from some box or another..

armanh:  I thought it was a 10/100 but I'd have to look it back up.  Picking up another cheap ethernet card and throwing it in is probably going to be my next step, since the others I've tried have all been wireless.

---

### Post by istara on 2007-07-29
Another observation:

Ubuntu is disabling IRQ #9 on startup.  Now, according to Windows, IRQ 9 is assigned to "Microsoft ACPI-Complient system" and I'm not entirely sure if or why that might be the cause of my symptoms.  A quick google search did return that IRQ 9 is usually the onboard sound, however, so could be causing some kind of conflict ([link]("http://discussions.virtualdr.com/archive/index.php/t-163263.html")).

BUT, while sifting through IRQ assignments in Windows, I also noticed that the Realtek card is sharing IRQ 18 with "VIA USB Enhanced Controller " and that the Creative Sound card is sharing IRQ 17 with "VIA rev 5 USB Universal Host Controller."  

This seems to be a good place to start considering that I can't get Ubuntu to detect my USB ports either..

I've never dealt with IRQs before, and certainly not conflicts or sharing between them.  But is it possible that mine have gotten tangled up, and if so, what's a good start to fixing them?

Thank you!

---

### Post by Pragmatist on 2007-07-29
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

---

