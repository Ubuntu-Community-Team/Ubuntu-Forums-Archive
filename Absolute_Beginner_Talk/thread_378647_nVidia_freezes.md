---
title: "nVidia freezes"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Jubal Slone on 2007-03-07
On a scale of one to ten with Linux fluency, I'm almost a 4, so I'm not a total newbie, but I've really been reading a lot to try to keep on top of the learning curve.  I'm a former professional Windows troubleshooter, so I know my way around computers, but I'm sick of Microsoft and now I'm using my girlfriend's new computer as a good excuse to teach myself Linux.  But, I'm having some troubles, so I'm turning to the community for help.

I'm running Ubuntu 6.06.  I have a GeForce 7100 GS PCI-e.  

I followed the directions from [www.nvidia.com](www.nvidia.com) and installed NVIDIA-Linux-x86-1.0-9746-pkg1.run a week or so ago.

It functions great now: my screensavers flow smoothly and I even have World of WarCraft: TBC running through wine and Maya for Linux runs like a charm.  

The problem I have are crashes that cause the entire system to freeze.  I first thought it was just a problem with wine or with WoW, but now when I run the GL screensavers, I get full screen freezes that are only fixable by a hard reset.  (Ouch.)  They're very frequent in WoW and a bit less frequent in the screensavers, but they often appear after ten minutes, very rarely sooner.  I never have a video problem when just running the desktop.

If this is the wrong board in which to post, please let me know, but I figured it'd be a good place because, while I am learning, I'm still a beginner.

---

### Post by Perfect Storm on 2007-03-07
Do you have beryl or any other Desktop enhancement running?

---

### Post by Jubal Slone on 2007-03-07
No.  No eye-candy until I get this sorted out.

---

### Post by Perfect Storm on 2007-03-07
Hmmm...It could be a driver bug. If you have the time try an earlier driver and see if it runs better with it then we can conclude if it's a bug.

What about the nvidia driver that comes through ubuntu's repo, are they supporting you card?

---

### Post by Jubal Slone on 2007-03-07
Well, I could try a newer version.  I think .9755 is out.  Or should I try an older one?

---

### Post by Perfect Storm on 2007-03-07
Give it a whirl, they might correct the error.

---

### Post by Jubal Slone on 2007-03-07
I updated the nvidia drivers and I thought it was going to work.  I ran WoW for about half an hour, then it did the exact same thing:  the screen froze, the mouse froze, and nothing at all responded.  I hard restarted and now I'm here posting again.

It might be hardware related.  My HDD and my RAM are both fine (I've ran diagnosis on both) but it possibly could be my graphics card.  What would be a good way to tell?  

Of course, it could also be software related.  Any suggestions?

---

### Post by Perfect Storm on 2007-03-07
Do you have another video card to test (best if it's a nvidia card) to see if it's the card itself.

---

### Post by Jubal Slone on 2007-03-07
Nope.  What are some software side things I could do to check?  

I'll get ahold of a PCI-e card if possible, but I'm not entirely convinced that's what it is.  I just am not ruling out the possiblity.

---

### Post by Jubal Slone on 2007-03-07
Okay, it's a problem that doesn't just affect wine/WoW.  I installed Armagetron and the same crash happened about five minutes into the game.

---

### Post by Jubal Slone on 2007-03-08
My problem's growing.  Now even outside of 3d apps, the screen and mouse will freeze requiring a hard restart.

---

### Post by Jubal Slone on 2007-03-08
Anyone?  I thought Linux wasn't supposed to randomly crash.  If I wanted random lockups, I'd switch back to XP.  :(

---

### Post by freebird54 on 2007-03-08
Which screensaver was it that hung you out to dry?  I don't use nVidia - but I have loackups with certain screensavers, and occasionally with wine.  I am beginning to suspect a library call made by video drivers as the problem (?)

Hope someone has some good ideas soon - or that Feisty fixes it.

---

### Post by Jubal Slone on 2007-03-09
I noticed it on GLMatrix, Skyrocket, and StonerView.  It's frozen mid-fade into the screensaver too.

If you think Fiesty might fix it, do you have a good link to read about upgrading from Dapper without a format?  (If that's even possible.)

---

### Post by freebird54 on 2007-03-09
The comment about Feisty was a hope - not an expectation.  However, as I understand it the upgrade path must be followed step by step (from Dapper to Edgy, then Edgy to Feisty) - so if your /home is on a separate partition you might want to install it from scratch....

I would suggest asking in the Feisty forums if anything is known about this - might at least give a hint if they are trying to fix it!

---

