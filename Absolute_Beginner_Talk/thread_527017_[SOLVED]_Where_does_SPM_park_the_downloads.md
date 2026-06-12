---
title: "[SOLVED] Where does SPM park the downloads?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by nuddernuby on 2007-08-16
Could someone be kind enough to tell me:
1.  where SPM stores the packages it downloads from the depositories?
2.  if it's possible to install the same programs on other computers on the LAN using these downloads (to save bandwidth)?
Thank you in advance

---

### Post by RomeReactor on 2007-08-16
Hi. Take a look in **/var/cache/apt** and **/var/cache/apt/archives**. You could use them to install on another computer, provided it also runs your version of Ubuntu, for the same architecture (32 or 64 bit, Power PC, or Sparc), and you also copy the dependent packages of the program you intend to install.

---

### Post by nuddernuby on 2007-08-16
Thank you, RomeReactor.
That did the trick.  Installed successfully.

---

