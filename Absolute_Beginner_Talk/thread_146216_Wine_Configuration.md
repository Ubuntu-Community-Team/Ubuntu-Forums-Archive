---
title: "Wine Configuration"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by agent_shooter on 2006-03-17
I installed wine for DVD backups.  I also installed DVD Shrink (3.2.015).  I went to change the dvd rom drive to a CD drive and not a local hard drive but somehow DELETED the C drive.  Now every time I run winecfg I get a error stating that there is no C drive and that I should ADD one.  I add and apply but nothing seems to save.

Anyone have some help for a newbie?

Thanks
Agent S

---

### Post by dcstar on 2006-03-17
[QUOTE=agent_shooter]I installed wine for DVD backups.  I also installed DVD Shrink (3.2.015).  I went to change the dvd rom drive to a CD drive and not a local hard drive but somehow DELETED the C drive.  Now every time I run winecfg I get a error stating that there is no C drive and that I should ADD one.  I add and apply but nothing seems to save.

Anyone have some help for a newbie?

Thanks
Agent S[/QUOTE]
If you don't mind going through the process of re-installing your Windows apps in wine, rename the hidden .wine directory on you Home directory and a fresh default wine environment will be created next time you run winecfg.

---

### Post by agent_shooter on 2006-03-17
Excellent work!

I deleted the .wine directory and ran winecfg and everything was good after that.

Thanks so much for your help,
Agent S

---

