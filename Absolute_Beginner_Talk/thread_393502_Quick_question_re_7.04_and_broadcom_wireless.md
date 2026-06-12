---
title: "Quick question re 7.04 and broadcom wireless"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by edmicman on 2007-03-25
I grabbed the beta for 7.04 and loaded up the live cd.  My wireless didn't work; I have a Dell 600m with a Dell Wireless 1450 miniPCI card.  From what I gather, this is a Broadcom chipset and from the posts it sounds like I have to use the ndiswrapper thing?  

Basically my question is, to get my wireless to work in Feisty, is there a better way yet than the ndiswrapper stuff?  It sounds like that's a royal mess still, and I'm not sure I really want to invest in the time to try and get it working (especially since I saw somewhere I might have to redo it if I upgrade the kernel?).    My XP installation has recently become hosed, so I was considering jumping into desktop linux with the Feisty release.  But if it's still a pain to get the Broadcom wireless working, I'll probably just wait it out.  Thanks for any info!

---

### Post by cowlip on 2007-03-25
I think the only way with that card is ndiswrapper: [http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092)

Other broadcom cards do now work with Feisty out of the box, but not this one.  Of course that's Broadcom's fault because the ones we do have were only reverse engineered from the wrt54g..but anyways..

---

### Post by nayo on 2007-03-25
You know what?  I had trouble getting ndiswrapper to work on Feisty with a Dell 600 and then when I reinstalled Dapper, wi-fi worked "out of the box".  I have no idea why but I'm not complaining.

---

### Post by johnnymac on 2007-03-25
Hey guys....your better off using fwcutter (Firmware cutter) IMHO.  I used ndiswrapper for a bit but have moved over to fwcutter - works so much better for me.

---

