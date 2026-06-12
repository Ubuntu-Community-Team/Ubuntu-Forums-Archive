---
title: "Ti-Book Keyboard Backlight Jaunty 9.04"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by genepool on 2009-04-29
On a 1.25GHz G4 Ti-Book I had the keyboard back-light working in 8.10 using these [_instructions_]("https://wiki.ubuntu.com/PowerPCFAQ#Keyboard%20backlight").  After upgrading to Jaunty 9.04 I get the following error messages:
```
>sudo modprobe ic2-dev
WARNING: All config files need .conf: /etc/modprobe.d/lrm-video, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module ic2_dev not found.
```
Any ideas/fixes?

---

### Post by genepool on 2009-06-04
bump

---

### Post by Lingonsylt on 2009-06-05
Have the same problem. Would also really be happy if anybody know how to fix it.

---

### Post by sdas on 2009-07-25
Yah, there was a typo in the FAQ.  I've corrected it now.

I've confirmed this on a 15" 1.67MHz G4 TiPB.

Cheers!

BTW:  Can't help you with those modprobe errors, got nothing.  Try the corrected steps and see if the corrected **/etc/modules** clears it up.

---

