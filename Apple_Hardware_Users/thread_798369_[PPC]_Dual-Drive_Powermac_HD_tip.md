---
title: "[PPC] Dual-Drive Powermac HD tip"
date: 2008-05-18
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-18
I was browsing through some of the OSX forums and found something interesting that might help Powermac tower owners with dual drives, or dual-drive cards with only a single drive...

This could be an urban legend, but it appears that if you have trouble installing onto these machines, normally the first hard drive jumpers are set to "cable select" and the second HD is set to "slave".

In some cases, especially if the drives are replacements, installation issues on the HD's are sometimes cured by specifically setting the primary drive as "master" instead of cable-select, and in all cases the secondary drive is set to "slave".

I don't own a dual-drive powermac, but it would be interesting to see if this in fact does help installation, or is just an urban legend. :)

---

### Post by frog_pilot on 2008-05-18
I own a g4 tower with 3 busses. on two of them there are attached 2 drives. One with two otical drives and one with 2 Hds. On the third there is a singel Hd attached. The single one is attached to the end of the cable, since this position determines its setting to master. I think otherwise you would run into trouble.

For some reason the 2 optical drives had the setting mentioned by you. One was set to 'slave' and the terminating (original) device was set to 'cs'. Ubuntu recognized these drives without problems. but on OS X.4 there was a strange behaviour. It didn't recognize the two drives after putting a cd in each and then removing one of them.

Since then I switched all drives to 'cs' as  suggested by apple. Now the position at the cable determines the master/slave setting and everything runs fine. 

For Linux I attached a second hd with 'cs' setting in slave-position. Whole installation (incl. yaboot) on this second hd went fine (first with 7.04 and now with 8.04, both clean installs).

---

### Post by stream303 on 2008-05-18
Nice info!

I guess this is one thing to watch for when receiving a unit second-hand after a user-mod may have been done only half-way. :)

---

