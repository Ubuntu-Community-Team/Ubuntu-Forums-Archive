---
title: "Firefox on PPC."
date: 2015-12-02
forum: Apple Hardware Users
---

### Post by protoss96 on 2015-12-02
Hi,  I am using powermac g5 with ubuntu 12.04, everything works fine but ppc developers are not compiling firefox or similar upgrades to use on ppc.... i am still on firefox 39 and i latest version because of web development... I tried to compile firefox 42/44 but its requiring at leats gcc 4.7, so i compile gcc 5.2.0 and its working perfectly, but firefox will not compile because of stupid reasons unknown to me... i don't want to upgrade to a newer version of ubuntu since 12.04 is still supported *i hope*... and 14.04 gives me constant kernel panics....

---

### Post by howefield on 2015-12-02
Thread moved to the "*Apple Hardware Users*" sub forum and unhelpful title amended.

---

### Post by tgalati4 on 2015-12-02
Unfortunately, doing development normally means using the latest compiler (like gcc 5.2), so things like Firefox and Chrome tend to be developed and compiled using the latest build tools.

So, you can either try to build gcc 4.7 on your 12.04 system (rather than 5.2) or make your system dual-boot with 14.04.  The Agony Units will probably be the same.  As for kernel panics, try using 14.04 (not 14.04.3) with the oldest kernel available (3.13 perhaps) and see if your system boots.

Trying to do development on a 10-year-old PPC is a noble effort.  A newer, x86 computer would be easier to maintain.  Yes, in principle, you should be able to set up the G5, but the Agony Units may not be worth it.

---

### Post by protoss96 on 2015-12-02
> **tgalati4 said:**
> Unfortunately, doing development normally means using the latest compiler (like gcc 5.2), so things like Firefox and Chrome tend to be developed and compiled using the latest build tools.  So, you can either try to build gcc 4.7 on your 12.04 system (rather than 5.2) or make your system dual-boot with 14.04.  The Agony Units will probably be the same.  As for kernel panics, try using 14.04 (not 14.04.3) with the oldest kernel available (3.13 perhaps) and see if your system boots.  Trying to do development on a 10-year-old PPC is a noble effort.  A newer, x86 computer would be easier to maintain.  Yes, in principle, you should be able to set up the G5, but the Agony Units may not be worth it.  yes, i expected that words... i am to lazy to again compile gcc .. . another 5-6 hours of waiting xd btw i will try lubuntu 14.04 but with 3.2 kernel.. because 3.2 is working without problems.

---

