---
title: "Wine and installers.. And Win Registry"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-11-16
What does WINE do to installer programs? What about programs such as installers that put entries in the registry. 

How can we use wine to run a beta that expires in a given amount of time inside of linux, only have the trial time never be exceeded.
Thanks.

---

### Post by inversekinetix on 2007-11-16
wine writes registry info to a fake regfile inside wine.  you could try modifying that registry using the wine   regedit tool that was installed with it.  The only legal way you could have the timed trial version last forever would be to pay for it.

---

