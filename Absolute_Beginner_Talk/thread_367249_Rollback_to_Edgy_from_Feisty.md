---
title: "Rollback to Edgy from Feisty"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by haricharan on 2007-02-21
Hi,

Is there a way i could rollback to Edgy from Feisty? Many of my applications not working properly due to the upgrade!!.. Main cause i believe is the xorg...my beryl, xine and my gtk applications that i m creating are not properly working..i dont see the transparency effects anymore with my applications..... Would Feisty allow a rollback of Xorg to a lower version?

---

### Post by Luk0r on 2007-02-21
That's the risk you take when beta testing, but I'm sure you already know that.  What about removing xorg through apt-get, changing the repos back to edgy's ones, then reinstalling xorg?

If you need the step-by-step commands for doing that, just let me know.

---

### Post by haricharan on 2007-02-21
yeah i know the drawbacks of beta testing......i feel i wont rollback to edgy....i would rather wait until this issue has been fixed....i would just try the xorg alone.....but how can find the previous versions??

---

### Post by Luk0r on 2007-02-22
The edgy repos would contain the previous versions, so just go into your sources.list, delete the sources, and replace them with an edgy repo file's entries.  An example can be found [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories").  Then just reinstall xorg, and you should get the edgy version.

---

