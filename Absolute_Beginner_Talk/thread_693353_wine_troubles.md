---
title: "wine troubles"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-10
hi

Installed wine, and then installed guild wars.  Everything was working but the video kind of sucked.  So I updated my video card drivers using envy and now wine doesn't work.  Do I need to uninstall it and reinstall it?

---

### Post by JoshuaRL on 2008-02-10
Not sure, but you might.  I would always suggest using the newest version of Wine instead of the (sometimes) much older version in the repos.  That is, unless you are sure the older version completely supports your program and stability is what you're after.  Try:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update && sudo apt-get install wine

```

---

