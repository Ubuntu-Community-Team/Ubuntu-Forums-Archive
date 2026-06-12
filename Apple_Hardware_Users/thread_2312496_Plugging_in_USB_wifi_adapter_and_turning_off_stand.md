---
title: "Plugging in USB wifi adapter and turning off standard driver killed builtin wifi"
date: 2016-02-04
forum: Apple Hardware Users
---

### Post by Zorgoth on 2016-02-04
My wifi has been acting up, so I ordered a USB wifi adapter off the internet for my Macbook Pro 11,2. The adapter didn't work on Ubuntu out of the box (though it claims to work on Linux), but while testing this, I turned off the broadcom driver in Additional Drivers. Now I can't turn the driver back on, despite multiple restarts and removing the USB adapter. The builtin wifi still works in OS X. I am completely unable to access the internet from Ubuntu.

Does anyone have any idea what I can do to fix this?

---

### Post by Zorgoth on 2016-02-04
Update: I still can't use wifi on my standard Ubuntu installation. I *can* use wifi when I boot up Ubuntu from a boot disk, so it's not a hardware issue. When I boot Ubuntu from my USB stick, I can load the driver; the bar almost immediately goes to ~50% then ~75%, stop for 10 seconds or so, then finishes and the driver is enabled.

On the installation on my computer, however, when I try to load the driver, it gets to ~50% and immediately stops trying and I'm back where I started.

---

### Post by Zorgoth on 2016-02-04
I fixed it by running

sudo apt-get purge bcmwl-kernel-source

and then reinstalling by downloading the package manually from the repository using my Ubuntu USB stick, then booting into my main ubuntu installation and installing the package with

dpkg -i name_of_package.deb

---

### Post by Zorgoth on 2016-02-04
I fixed it by running

sudo apt-get purge bcmwl-kernel-source

and then reinstalling by downloading the package manually from the repository using my Ubuntu USB stick, then booting into my main ubuntu installation and installing the package with

dpkg -i name_of_package.deb

---

