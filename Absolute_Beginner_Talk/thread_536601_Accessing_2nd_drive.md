---
title: "Accessing 2nd drive"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by medley on 2007-08-27
Hi all. I'm sure this has been asked before, but I haven't really found the specific answer I'm looking for. I have 2 80gig drives in my Kubuntu box. I've partitioned both, and created a mount point on each one. However, it appears that when I check the properties for the 2nd drive, it is actually referring to the primary one. The space used vs free is identical for each. When I use QtParted to look at the second drive, it shows 74gig free, but when I check the properties of Drive2 using Konq, I see the same free as on Drive1 (58gig). So I don't think I'm actually referring to drive 2 when I access the mount point. Does this make any sense?

---

### Post by medley on 2007-08-27
Nevermind....resolved. I needed to preceed the mount point name with '/'. Works fine now.

---

