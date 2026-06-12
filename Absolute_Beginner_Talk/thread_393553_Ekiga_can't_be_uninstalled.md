---
title: "Ekiga can't be uninstalled???"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by suntin on 2007-03-25
I just tried to uninstall Ekiga, not using it so why keep it on disk...

It can only be uninstalled through the Synaptic manager because of dependacies.
Oddly the dependacy is "Ubuntu Desktop" surely that can't be right, why on earth would the desktop system rely of a VOIP module to function???

In fact this is now the cause of some concern because it feels like I'm having network software forced on to my system...:(

---

### Post by xXx 0wn3d xXx on 2007-03-25
The Ubuntu-desktop package is a meta package and is basically a "list" that contains the names of all the applications on a clean install. There is no harm in removing it. Just be sure you re-install it before attempting a dist-upgrade.

---

### Post by jeffathehutt on 2007-03-25
ubuntu-desktop is actually a meta package.  It doesn't include any actual programs.  The only real reason you need it is to upgrade to another version of Ubuntu, like going from edgy to feisty.  It is safe to remove ubuntu-desktop.

---

### Post by cowlip on 2007-03-25
If the ubuntu-desktop metapackage only recommended Ekiga instead of a dependancy, it would be fine, but right now it doesn't.  Maybe in a future release...

---

### Post by cntrtrst on 2007-04-09
That's a bad situation.  It's manipulative and should be changed.

---

