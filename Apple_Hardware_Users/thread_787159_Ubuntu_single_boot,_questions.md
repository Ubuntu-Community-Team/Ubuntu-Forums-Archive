---
title: "Ubuntu single boot, questions"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by CodeSamurai on 2008-05-08
Hello all.  I've completely switched over from OSX to Ubuntu 8.04 now.  I've scoured these forums and only found half answers, that's why I'm posting my own thread.  Here is my question:

If I completely wipe my hard drive and install Ubuntu, what would the repercussions be?  I know macs use a different type of boot loader, and having no OSX means having no rEFit.  How would this affect Ubuntu? Would I still be able to boot? I wouldn't be able to get firmware updates anymore, but I can always reinstall if there is one I really need.  Does anyone have any experience with this?  Let me know.  Thanks!

Trent out

---

### Post by cyberdork33 on 2008-05-08
you might get a long pause at startup but that is all.

---

### Post by tylermoody on 2008-05-09
If you dedicate your entire hard drive to Ubuntu, it will install the GRUB bootloader. Your system will take a little longer to start up, but Ubuntu won't have any problems running. I had some trouble on my first try* installing Hardy, but the second attempt went through flawlessly. 

It is true that you will be unable to get firmware updates from Apple any more. Be sure that you're fully updated before abandoning OS X. 



* Originally I tried dual-booting Gutsy and a Hardy release candidate. The Hardy installer broke my master boot record. You shouldn't see this problem if you're doing a full-disk install.

---

