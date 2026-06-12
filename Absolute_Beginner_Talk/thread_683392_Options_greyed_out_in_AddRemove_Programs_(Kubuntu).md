---
title: "Options greyed out in Add/Remove Programs (Kubuntu)"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by RedStar1916 on 2008-01-30
Okay so I'm currently having trouble connecting to the internet through my college's proxy with newly installed Kubuntu 7.10. I think the problem would be solved if I could download and install Firefox. The trouble is though that whenever I go into Add/Remove Programs, all of the programs that I don't already have a greyed/faded out, and I can't click on them. This happens even when I connect via my girlfriend's direct internet connection, and all other aspects of the internet are working fine. I went into preferences and checked all of the download sources, tried multiple different servers and un-commented out all the different sources in sources.list. But it didn't do anything; all the options, including Firefox, are still greyed out and unclickable.

I have also tried "sudo apt-get install firefox", but all I get is this:
Reading Package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package firefox has no installation candidate

---

### Post by wolfen69 on 2008-01-31
it sounds to me like apt is corrupted. try uninstalling and re-installing.

---

### Post by drprozac on 2008-03-30
Its a bug.

Try to sudo dpkg --configure -a 

It will configure the remaining pkgs and will release the lock on your database.

---

