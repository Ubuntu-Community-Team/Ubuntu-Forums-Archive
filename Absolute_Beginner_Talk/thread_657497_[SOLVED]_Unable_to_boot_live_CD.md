---
title: "[SOLVED] Unable to boot live CD"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by bogstandard on 2008-01-03
Hi there!

I have recently (ie today!) purchased a new computer (HP dx2250, Athlon X2 5000+, 2GB memory, 250GB SATA HD, SATA Lightscribe dvdr, 250GB IDE HD, ATI Radeon Xpress 1150 (I will be putting in an nvidia soon!)). On my old system I had Daryna (linux mint twist on Gutsy Gibbon)  running brilliantly but on this one I am struggling!

The Live CD boots up and starts to load up and then dumps me into a "Limited Shell" (BusyBox IIRC). I tried a few suggestions (No splash, noapic etc) and nothing helped. So I followed another suggestion and changed the SATA settings in the bios - success! Well kinda - Daryna boots but the display dances around the screen, Gutsy Gibbon just hangs and PCLinuxOS fails at the ethernet configuration stage.

Any ideas? Shall I just try all of the suggestions in the wiki?

Thanks,
Stu

PS Happy new year to you all!

---

### Post by boban on 2008-01-03
What motherboard do you have?

---

### Post by bogstandard on 2008-01-04
Hi Boban - according to sisoft sandra it is a MSI 0A7C.

---

### Post by boban on 2008-01-04
Hmm... Can't find the spec of this motherboard anywhere... But I will try to guess (blind shot actually): have you tried the irqpoll option?

---

### Post by bogstandard on 2008-01-04
I'll give it a try when I get home _ wish me luck!

---

### Post by bogstandard on 2008-01-04
Tried with boot option irqpoll and the boot hang up at the splash screen with the Caps Lock and Scroll Lock lights flashing.

Tried setting the graphics to 1400x?x? with the irqpoll option and it booted further this time - it started to load gnome and nautilus and then fell back out to the regular login screen. It then just loops repeatedly!

---

### Post by boban on 2008-01-05
Have you tried the alternate ubuntu cd?

---

### Post by bogstandard on 2008-01-05
Sorted now - new graphics card and its done!!!

The following is copied from the Mint forums incase anyone else gets this problem...

[I]Right then, graphics card came yesterday so I fitted it today.

The cd now boots!!! :shock:

When the desktop loads up I get an error message (failed to connect to socket /tmp/dbus_TgUAQLmjoA connection refused) and the lovely mint theme is missing. (I have uploaded a screenshot for you! [http://files.mint-space.com/getfile,200](http://files.mint-space.com/getfile,200) ... t.png.html

Any ideas?

Success!!!!!

Changed the SATA setting back to legacy from IDE and now Mint looks real good!

Well pleased now![/I]

Thanks for your help boban!!

---

### Post by boban on 2008-01-06
I'm glad you solved the problem :)

---

