---
title: "vlc asks for wxvlc, and wxvlc asks for vlc - isn't this crazy?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-12
The fact is my box runs Ubuntu 5.10 and has no internet access. So I just can't "apt-get install vlc". Instead, I had to manually download deb packages from packages.ubuntu.com (vlc and its dependencies) on another machine.

However, when I try to install **vlc**, it says that it cannot be installed because **wxvlc** is not installed/configured. So I dpkg -i **wxvlc**. But **wxvlc** says that it cannot be installed, as **vlc** is not installed.

This is driving me crazy. Give me some ideas, please.

---

### Post by trent dillman on 2006-04-12
Install both with one dpkg command...

or, try to install both then ```
sudo apt-get -f install
``` (no net needed for this)

---

### Post by zugu on 2006-04-12
As in:

**sudo apt-get -f install vlc_package_name.deb wxvlc_package_name.deb**

????

---

### Post by dvarsam on 2006-04-13
Dear "zugu",

Try to install those co-dependent ".deb" files, like this:

> dpkg -i package_name1.deb package_name2.deb

The above should work with NO problem, because it installs Both (as if they were one package)...

Note:
If you had more co-dependent packages, you would just add them (too!), right-after the last package name.

Good Luck!

---

