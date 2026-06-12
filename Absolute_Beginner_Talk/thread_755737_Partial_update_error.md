---
title: "Partial update error"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by hoodchica on 2008-04-15
I need a little help please. So I just installed Ubuntu 7.10 this week, and today I was asked to install some available updates. It said that due to some problems, not all updates can run, only partial updates. So I had to choose between partial updates or cancel the whole thing. I let the partial updates get installed, and guess what: several features are missing now, like windows animation, windows top bar, you know, where the close and maximize buttons are..MISSING.. I can't even click on the side to move the window... it won't move. I can only work with a certain window from file, edit, view, bla bla, menu. Can anybody give me some tips, please? 

:confused:

---

### Post by master5o1 on 2008-04-15
hmm I only ever had that kind of problem when incorrectly install compiz and getting errors between using compiz or just plain metacity before Ubuntu began including it by default.

if you can open a terminal try type sudo apt-get update and sudo apt-get upgrade to finish or fix the system... press CTRL ALT f1 if you need to access the tty terminal, CTRL ALT f7 to return to the gui.

Did it have a kernel upgrade or anything? if you were using a restricted video driver it is possible that the ubuntu-restricted kernel hasn't come through yet which means upgrading in a few hours again might even fix the problem if it doesn't now.

---

### Post by hoodchica on 2008-04-15
ok, you are right, it is about compiz. "compiz-fusion-plugins-extra:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed"  this is the error that i get. so compiz is installed and upgradeable,  but has unmet dependencies. how can I solve this?

---

### Post by zvacet on 2008-04-15
@ **hoodchica**

>  It said that due to some problems, not all updates can run

What kind of problems?Do you have all repos open?Look in system<admin>software sources<check all under ubuntu software and updates tab.Reload.

```
sudo apt-get update && sudo apt-get upgrade
```

Did you try to make distro upgrade?I ask this because libpango1.0-0 (>=1.18.3) is Hardy package.

---

### Post by hoodchica on 2008-04-15
thanks, it's working now, I enabled more ubuntu updates, and it was able to complete installing the update.

---

