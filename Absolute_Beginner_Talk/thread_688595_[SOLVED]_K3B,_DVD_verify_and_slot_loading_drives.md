---
title: "[SOLVED] K3B, DVD verify and slot loading drives"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by siddartha on 2008-02-05
Hello,

I have an external slot loading slim DVD writer driver and checking the verify option for burning, yet if the disk is ejected there is a fail for the verify process. Is there a workaround or just something the authors missed?

Cheers,
Sidd

---

### Post by LowSky on 2008-02-05
how is the disk being ejected, by the system or by rthe user? Could it be that it is actually failing verification? If your ejecting it, it is going to fail because your making it fail.

---

### Post by laidback on 2008-02-05
If I remember correctly when I check the verify option in K3b it burns the CD/DVD, ejects it, then reloads it in order to perform the verify. Don't remove the cd/dvd after it's been burned and before the verification process, leave it to be reloaded (that is the draw will close again) and verified, then it will be finally ejected.

---

### Post by siddartha on 2008-02-05
1. it is ejected by the k3b. even if i'd want, i think (hope) the unit is locked
2. once it ejects the cd it can't catch it back so it should wait for the disk to be reinserted or something like that

---

### Post by laidback on 2008-02-06
Should not need any intervention on your part after you have clicked for the burn, K3b handles it all. What I'm saying is that after the burn the drawer will open, but then K3b closes the drawer and starts the verification process, so don't remove the cd when the drawer first opens as this will cause verification to fail.

---

### Post by siddartha on 2008-02-06
> **laidback said:**
> Should not need any intervention on your part after you have clicked for the burn, K3b handles it all. What I'm saying is that after the burn the drawer will open, but then K3b closes the drawer and starts the verification process, so don't remove the cd when the drawer first opens as this will cause verification to fail.

Dude, it's a slot loading mechanism. You have no drawer.

---

### Post by mc4man on 2008-02-07
I believe it's a known issue with some unmotorized tray and slot load drives
try Settings->Configure K3b->Advanced->Miscellaneous->Do not eject medium after write process

---

### Post by siddartha on 2008-02-09
Thanks. I wasn't aware of this feature/option. I will test it as soon as I write a new DVD.

---

### Post by mc4man on 2008-02-11
If you still have issues and have no "bias" towards running wine then ck. out Imgburn
[http://www.imgburn.com/](http://www.imgburn.com/)
The newest version is quite a remarkable prog - see changelog, guides, ect.

---

### Post by siddartha on 2008-02-11
I have quite a few apps running fine on Wine, yet, it should be a shame to have a need to switch for such a basic task as writing a CD/DVD. More, apart this issue with the verify process I have nothing to say against K3B. Once more I have to dump Gnome apps and run KDE apps in a Gnome environment.

---

