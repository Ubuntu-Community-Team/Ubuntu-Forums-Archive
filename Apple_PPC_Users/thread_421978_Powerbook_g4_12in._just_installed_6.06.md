---
title: "Powerbook g4 12in. just installed 6.06"
date: 2007-04-24
forum: Apple PPC Users
---

### Post by Platonjk on 2007-04-24
hey guys, im a complete newbie to linux OS. hell i've never really used the Mac OS that much either. but ubuntu caught my eye after seeing a friend use it.

so apparently the broadcom 4306 wifi adapter built into my laptop wont work on any version of ubuntu? at the time atleast.

so for the time being which brand usb wifi adapter would be best to use? do the trendnets work well?

---

### Post by stmiller on 2007-04-24
Please use the search feature. As you can imagine, this has been asked before.

I would suggest using Feisty, as it has lots of PPC fixes. Esp for Airport Extreme.

In Feisty you can just apt-get install bcm43xx-fwcutter and it will work.

Ubuntu cannot include the firmware for this driver b/c of the license.

---

### Post by Platonjk on 2007-04-25
i did that(in fiesty)

and its saying

E; could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: unable to lock administration directory (/var/lib/dpkg/), are you root?

---

### Post by stmiller on 2007-04-25
type 
sudo apt-get .......

---

