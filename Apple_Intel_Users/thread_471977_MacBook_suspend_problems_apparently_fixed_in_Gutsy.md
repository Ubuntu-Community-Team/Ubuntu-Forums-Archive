---
title: "MacBook suspend problems apparently fixed in Gutsy"
date: 2007-06-12
forum: Apple Intel Users
---

### Post by thully on 2007-06-12
I just tested a bare metal (not VMware) install of Ubuntu Gutsy (development branch) on my MacBook Core Duo, and apparently Gutsy fixes one of my major gripes with Ubuntu on the MacBooks.  In Gutsy, suspend-to-RAM works perfectly fine - it takes 1-2 sec to suspend, and another 1-2 to resume.  Unfortunately, the trackpad is still craptastic and it runs quite hot as usual - I dunno if I'll stick with or do VMware Fusion (with Gutsy - I like messing with the development branch :) )

---

### Post by benanzo on 2007-06-12
I'm not sure that suspend-to-ram is that widespread of an issue even with Feisty.  I know that some have trouble, but I don't.  I have a first-gen MacBook with Core Duo and suspend/hibernate both work out of the box for me.  The only thing I can think is that there is some hardware discrepancy between some of these machines that prevents it from working.  I have noticed no difference even in Gutsy.

---

### Post by ronocdh on 2007-06-12
> **benanzo said:**
> I'm not sure that suspend-to-ram is that widespread of an issue even with Feisty.  I know that some have trouble, but I don't.  I have a first-gen MacBook with Core Duo and suspend/hibernate both work out of the box for me.  The only thing I can think is that there is some hardware discrepancy between some of these machines that prevents it from working.  I have noticed no difference even in Gutsy.
C2D MBP here, never got suspend working. The computer never wakes from suspend to disk, and suspend to RAM just doesn't work, the computer immediately "wakes up" and it goes to a locked screensaver. =/ I guess I'll test with Gutsy sometime soon, maybe Tribe 2.

---

### Post by thully on 2007-06-12
With you mentioning it, I'm starting to have another thought as to why I can suspend now.  I'm thinking it may not in fact be Gutsy, but the fact that my system was recently repaired and had the logic board replaced.  I figure that maybe only the early logic boards have issues with suspend.  Will test w/ feisty and see if this holds up - if so, I guess the issue still holds for some MacBook/MacBook Pro owners - but not others.

---

### Post by ronocdh on 2007-06-13
> **thully said:**
> With you mentioning it, I'm starting to have another thought as to why I can suspend now.  I'm thinking it may not in fact be Gutsy, but the fact that my system was recently repaired and had the logic board replaced.  I figure that maybe only the early logic boards have issues with suspend.  Will test w/ feisty and see if this holds up - if so, I guess the issue still holds for some MacBook/MacBook Pro owners - but not others.
Interesting. Please post back with Feisty results!

---

### Post by thully on 2007-06-13
I can confirm Feisty does NOT suspend, as always, except when I patch the kernel using the known workaround (mentioned on here). Gutsy works out of the box and does so perfectly. That's good news for MacBook users who can't suspend - Gutsy apparently resolves the issue.

---

### Post by russo.mic on 2007-06-14
I've got a Macbook Pro C2D and never got suspend to work, although I didn't give it a ton of effort.

Some of these threads have got my mouth watering for Gusty.  Maybe I'll do a disk image and give it a shot...

---

### Post by incubus on 2007-06-14
It's too bad suspend is such a strange issue: it works for some, it never works for others.  I was on Feisty since the early betas and it didn't work for me.  Then I did a fresh install and now it works, out of the box.

Wait, now that I think more about it, the one thing that I had wrong before is that I didn't have a swap partition.  See, I'm using rEFIt and one partition is for EFI, the other one is for Mac OS, another is for Ubuntu, and the rest I made for my data (ext3fs).  So I didn't have a swap partition (the limit of 4 primary partitions).

For a few days I forgot to make the swap file (don't try this at home).  After I did it, I tested suspend to RAM and it worked.  So in my case, it seems, it was the swap partition missing.  Before this, the computer would not wake up.  Or it would, but I would just have a blank screen.

This is a Core 2 Duo, by the way.  I hope this helps somebody.

incubus

---

### Post by kzm. on 2007-06-14
it works with me right out the box with feisty on a macbook c2d....

---

### Post by jamesotron on 2007-09-25
I have a first gen MacBook Pro (Core Duo) and I can't seem to get either suspend or hibernate to work.  I guess thems the breaks.

---

### Post by alephsmith on 2007-09-25
s2ram worked on my Santa Rosa MBP with Tribe 5... once.

This is easily the feature I miss most when not in OSX (more than even hot plugging monitors).

---

### Post by cherry316316 on 2007-09-30
> **alephsmith said:**
> s2ram worked on my Santa Rosa MBP with Tribe 5... once.

This is easily the feature I miss most when not in OSX (more than even hot plugging monitors).


how did u installed gusty on macbook , did u have to go from any lengthy process, or was it as simple as on anyother laptop (which uses windows ) 

i want to install gusty on my macbook , and i plan to install only gusty and no Mac OS , is it possible ???

I have gusty on my dell , and its working fine except sound :(

---

