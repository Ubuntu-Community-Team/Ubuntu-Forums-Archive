---
title: "The ultimate beginner's error"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by charlieg on 2005-07-15
Well, new laptop sitting on the desk, and not wanting to go through the long haul that is Gentoo [that I run on my desktop machine], I went and grabbed the Ubuntu 5.04 install CD.

Since the only CD burner was on the laptop, with WinXP installed, I enjoyed the irony of using WinXP to create the CD that would wipe it off the machine.

Imagine my surprise when, upon rebooting, it wouldn't boot off the CD.  After 20 minutes of continuous rebooting and trying all sorts through the BIOS, I resigned myself to not installing Ubuntu and went to bed.

Fast forward 12 hours.  A good sleep and a bit of net browsing, googling for 'cd not bootable'.  Not finding much of use, I went to remove the install CD... only... the bloodey drive was a centimetre open already!  The damned CD burning utility had ejected the CD drive whilst I wasn't paying attention and, it being a laptop, had not pushed the tray out all the way!

So, the mystery of the unbootable bootable install cd now solved, Ubuntu is installing... ***waits patiently***

*Just to note, I'm not actually a Linux beginner [3 years of exclusive home usage and counting].  Still, this is the first time I've tried Ubuntu.*

---

### Post by apollo2011 on 2005-07-15
I think everyone has their silly mistake stories similar to yours! :)

btw, welcome to the Ubuntu forum!

I think you should find Ubuntu very easy to use, especially if you already know how to run Gentoo, which I am trying (haven't tried yet) to install on my desktop to play around with.

---

### Post by Mr. Electric Wizard on 2005-07-15
Dang, going from Gentoo to Ubuntu, your gonna love it man!
Are you going to try to get Wireless Access on your laptop?

---

### Post by maruchan on 2005-07-15
Heh, I've had a lot of "It's Linux's fault" moments like that, where it turned out to be my own error.

One time I spent a whole day trying to view a screen res higher than 640x480, finally added what I knew would fix the problem, rebooted, and...there was a flicker, then...nothing.

Turned out my monitor had unplugged itself :)

---

### Post by charlieg on 2005-07-15
**Mr Electric Wizard:** Yes, I will be.  Are you implying that it's easy or hard with Ubuntu?

**maruchan:** How long before you figured out it was unplugged?  :smile:

---

### Post by apollo2011 on 2005-07-15
[QUOTE=charlieg]**Mr Electric Wizard:** Yes, I will be.  Are you implying that it's easy or hard with Ubuntu?[/QUOTE]

I don't know what Mr Electric Wizard was implying but, unless you have a Broadcom Wi-Fi card (like me), it should be easy. If you do have a Broadcom Wi-Fi card, you will need to use Ndiswrapper and it is a longer more advanced procedure to get it to work.  In short, Ndiswrapper loads the Windows driver for the card because Broadcom is mean and doesn't make Linux drivers for their cards.  You can probably try "sudo lspci" to list your PCI cards and see what kind of card you have if you don't know.

---

### Post by maruchan on 2005-07-15
> maruchan: How long before you figured out it was unplugged?

Oh, sorry, I didn't mention that. Well, let's see. I smacked my head, hit the keyboard a few times, moved the mouse, and gripped the area of my chest that was starting to burn from within.

So, all told, probably about 30 seconds of "linux, you SUCK" :)

---

