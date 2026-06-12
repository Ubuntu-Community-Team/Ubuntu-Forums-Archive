---
title: "package &quot;type&quot; confusion"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by wesky on 2006-04-29
I'm thinking about installing ubuntu on my computer and I'm a little confused on the different "kinds" of packages. After reading a bit, I found that some packages are considered KDE packages and some considered GNOME packages. What exactly is the difference, why does the distinction exist? I know you can run KDE packages on GNOME and vise versa, but it's sometimes slower. Do all packages fall in one of these two categories? For example, GIMP is used widely on both desktops, does it have a KDE or GNOME designation? Or is it "neutral"?

Also, Wikipedia says that Ubuntu and Debian packages are not always compatible with each other. What does that mean? Are packages distro-dependent too?

Thanks.

---

### Post by Kethinov on 2006-04-29
KDE and GNOME use two different windowing toolkits. KDE uses QT and GNOME uses GTK. The Gimp was built with GTK, so it is a GNOME app.

Packages on the other hand are built for specific distros and have nothing to do with GNOME or KDE. Because Debian and Ubuntu are different distros, their packages may not be compatible with each other.

---

