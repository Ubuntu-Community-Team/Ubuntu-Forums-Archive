---
title: "boot menu doesn't show up; machine only boots OS X"
date: 2007-11-27
forum: Apple PPC Users
---

### Post by jmelton on 2007-11-27
After several successful boots of Feisty which I installed on my iBook G4 over the weekend, suddenly my machine will only boot into OS X and doesn't show a boot menu.  Has anyone else ever had this happen?  I assume that for some reason OS X has overwritten yaboot?  How can I fix this, and prevent it from happening again?

---

### Post by Auria on 2007-11-27
Hold down alt during startup, it should then allow you to boot ubuntu where you run something like ybin -v (do you own research, i say that from the top of my head) to bring yaboot back. This usually happens when you update OS X, and unfortunately i don't think there's a way to avoid that, you need to bring it back manually everytime

---

### Post by jmelton on 2007-11-27
Thanks; I discovered the solution to my problem with a little Googling around shortly after I posted my message.  Actually what I found that worked for me was holding down option-command-t-r during boot, but I gather that just holding down alt does the same thing.  Once I got in and ran ybin I was back in business.  Now, if I can only get my wireless to work (I think I'm getting close)!

---

