---
title: "Konqueror warning message on kubuntu 7.04"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-08-30
Hi There! running this command to read a pdf with konqueror:


fredscripts@laptop:~$ konqueror ~/LinuxDoc/LinuxNewbieAdministratorGuide.pdf
kparts: WARNING: Part '' has a widget view widget with a focus policy of NoFocus. It should have at least a ClickFocus policy, for part activation to work well.


And then konqueror runs the pdf perfectly, but why does that message appears?

Thank you very much!

---

### Post by igknighted on 2007-08-30
For some reason Ubuntu (maybe this comes from Debian?) builds KDE with the debug options compiled in.  Basically, as far as the end user is concerned, it means nothing.  Just ignore it.  It's not an error, just a warning (warnings imply that something isn't being done in the ideal fashion, but the system will do them just fine anyways).  If you want you can check bugzilla and either confirm a bug against this (if there is one already) or submit a new one (if there is no bug yet reported).

---

### Post by fredscripts on 2007-08-30
Thanks for answering!
If it's just a warning and doesn't imply any problem I'll get used to, but if someone knew how to avoid that warning message would be great :)

---

### Post by igknighted on 2007-08-30
> **fredscripts said:**
> Thanks for answering!
If it's just a warning and doesn't imply any problem I'll get used to, but if someone knew how to avoid that warning message would be great :)

;) recompile KDE without debugging.  Aside from that, sorry, if it's possible I'm not sure how.  I'm sure there is a good reason that they compile with debugging, but even the KDE folk aren't sure last I heard.

---

