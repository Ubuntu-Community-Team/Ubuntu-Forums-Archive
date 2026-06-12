---
title: "alltray install"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by BigRay5264 on 2007-02-08
Less than a week on Ubuntu,so bear with me...tried to install AllTray but installer said only one software management tool was allowed to run at the same time.Please close Update manager,Synaptic,or aptitude first....to my knowledge none of these was open...rebooted and tried sudo apt-get install alltray in terminal and got this---E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ...what do I have to do now?

---

### Post by Xappe on 2007-02-08
try to do as it says:
open a terminal and run

sudo dpkg --configure -a

---

### Post by BigRay5264 on 2007-02-08
> **Xappe said:**
> try to do as it says:
open a terminal and run

sudo dpkg --configure -a

I tried that but didn't work....forgot exactly what it said...but had updates to install,which led me to way to fix it...something was broken it said...sun java package I believe...fixed that and all is good

Thanks

---

