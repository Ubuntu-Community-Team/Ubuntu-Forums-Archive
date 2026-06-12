---
title: "Raid 1 software or hardware?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-26
I have my basic server set up and accessible. Now the question is one of RAID 1.  I have the second 500gb drive installed but not mounted.  What is the general concensus for a newbie?  Should I try and set up Raid 1 to get a mirrored drive or should I buy one of the inexpensive SATA controllers that are supposed to have RAID 1?

Thanks for any input.

---

### Post by toupeiro on 2007-11-27
Software RAID has more system overhead than hardware RAID, and also requires more interaction. (please note, It's been some time since I've done software RAID in Linux.  I have more experience with Software RAID in solaris.) 

I only use software RAID if I can't run the RAID level I want to run without spending $$$ on a high-end RAID controller, if a RAID controller is not available for the system I want a RAID array in, and/or Ithe system overhead of soft-RAID is not going to affect the purpose of the box.

My suggestion is to use hardware.  You will be happier in the long run, though software will be more of an educational endeavor.

---

