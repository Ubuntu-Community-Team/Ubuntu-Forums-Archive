---
title: "Back-up in Ubuntu 6.06-LTS?"
date: 2006-12-13
forum: Apple PPC Users
---

### Post by three-cushion on 2006-12-13
I now have a reliable version of Ubuntu installed, (result of a re-install + a 221MB update). Before I go off an an APP install binge, what is the simplist method for backup of the 3 Ubuntu partitons (containing ext3, swap, and Apple_bootstrap). I would like to point the backup to a 2nd internal HD that has plenty of room. Would also be nice if the back-up were bootable (eg, the bootstrap would work from the back-up drive).

I looked through the APP available list (Universe included) and saw nothing that would work.

Thanx in advance for any advice you have..

Jim B
PS What about all those PGP keys one *may* need? Work on those first downloading any APPs?
Run a list of sources.list first? Then if all are there, run:

*sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade*

in Terminal?

---

