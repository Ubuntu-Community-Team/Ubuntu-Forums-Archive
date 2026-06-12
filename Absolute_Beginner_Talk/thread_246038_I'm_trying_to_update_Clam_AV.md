---
title: "I'm trying to update Clam AV"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2006-08-28
I installed clamav and the "graphical front-end for ClamAV" (clamtk) from the synaptic packet manager. Everything seems to be going fine, but when I click "help" "update signatures" it tells me "You virus signatures are up to date". So I'm guessing my signatures are up to date even though I just installed it, is that possible?
Anyway, something related to that is when I check for the latest version by running "sudo freshclam" it tells me "Your ClamAV installation is OUTDATED!"
To be exact:

ClamAV update process started at Mon Aug 28 12:20:57 2006
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.2 Recommended version: 0.88.4
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
main.cvd is up to date (version: 40, sigs: 64138, f-level: 8, builder: tkojm)
daily.cvd is up to date (version: 1745, sigs: 2776, f-level: 8, builder: ccordes)

Can somebody tell me how to get the latest version?
I'm a Windows user trying to learn Ubuntu, so don't get too technical on me.
Thanks in advance
Jonathan

---

### Post by Kilz on 2006-08-28
> **metalaxesucks said:**
> I installed clamav and the "graphical front-end for ClamAV" (clamtk) from the synaptic packet manager. Everything seems to be going fine, but when I update it says "You virus signatures are up to date". Is this possible that its already up to date even though I just installed it?
Another question
Does it update automatically?
Thanks in advance
Jonathan

Yes, its most likly up to date. No it wont do much of anything automaticly, including update. Most Linux anti virus programs dont even have active scanners like Windows ones do, you have to manualy tell it to scan files. The reason is anti virus programs are a waste of time in linux. All the Linux viruses I have ever read about require you to do something stupid like run as root to work.

---

