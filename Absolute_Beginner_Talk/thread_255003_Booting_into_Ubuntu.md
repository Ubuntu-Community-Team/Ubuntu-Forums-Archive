---
title: "Booting into Ubuntu"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by BillA1016 on 2006-09-10
Hi. My friend just gave me an Ubuntu LiveCD today for Mac. I'm using it on an iMac G3. I can boot from the disk fine and everything goes fine, until I hear the entering Ubuntu sound, then the screen goes black. The computer sounds like its reading the CD, but the screen was black for about 20 minutes so I restarted. The same thing happened with the second boot into Ubuntu and its been black for about a half hour now. Is there something I should do or just wait it out? Thanks!

---

### Post by BillA1016 on 2006-09-10
Please help. Its been 45 minutes now since the screen went black and I have no idea what I should do.

---

### Post by mike3k on 2006-09-10
Sounds like it doesn't support that machine's video chip. It should come up right away with the Gnome desktop.

Did you see the boot messages scroll by in text mode before it tried to switch into graphic mode? Were there any error messages about device not supported or something like that?

---

### Post by meng on 2006-09-10
Definitely don't wait it out. That's too long, something's wrong. The possibilities - bad CD image download, bad CD burn, or just some other gremlin preventing the LiveCD from booting completely (not sure if this can happen on Macs, but it sure can happen on PCs). If you are sure you want to install Ubuntu, you can try the Alternate CD (but you'll have to download/burn it yourself). If you want to take the live desktop for a spin first, I don't have any other suggestions.

---

### Post by BillA1016 on 2006-09-10
Thank you. I'm going to try the LiveCD on my newer Mac to see what it does. The newer Mac is Intel though, so I'm not sure its compatible.

---

### Post by Darklighter137 on 2006-09-10
Last I heard, that architecture isn't supported at all.  =(

---

### Post by BillA1016 on 2006-09-10
Could changing color, resolution, etc effect whether I can see the desktop? I can see the screen where it says Ubuntu and the bar fills up and tells you the list of what its doing.

---

### Post by BillA1016 on 2006-09-11
Anyone have any new ideas?

---

### Post by bulldog on 2006-09-11
It's a MAC and I don't know if you can install Ubuntu on it.

What's wrong with Tiger OSX?

But can't help you with it.

---

### Post by BillA1016 on 2006-09-11
iMac G3's are too slow and incapable of running Tiger. Mine doesn't have the RAM speed to run any version of OSX. I have Tiger on my laptop but want Ubuntu on the older computer. The G3 has OS9 on it right now, which can't get into the college's network. I've been told Ubuntu Dapper Drake can.

---

### Post by Eldar11 on 2006-09-11
ya G3 can be weird, mine wouldn't even boot from the PPC CD, and I had to go get a different computer, to install ubuntu, and that one's messed too, so i don't know

---

### Post by Metacarpal on 2006-09-11
Hey all - found the answer while researching Bill's problem in a different thread:

If you are using a pre-pressed CD (one with the Ubuntu label) or if you downloaded the 6.06 version (before 6.06.1 was released), there was a problem with the installer that made it incompatible with a small selection of Macs, including the 333MHz G3s.

Solution: go download a new iso and burn the CD.  The iso file currently available is the 6.06.1 release, which apparently has corrected that problem (and it has a bunch of updates packaged in, so there's less downloading once installation is done).

---

