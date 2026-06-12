---
title: "Uninstall avast! Anti-Virus"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Kemik88 on 2007-01-24
Hello,

How can I uninstall avast? I used [this]("http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html") guide to install it, but it gives errors when I try to start avast now so I'd prefer to just get rid of it.

I've checked the add/remove list in the Applications menu but avast isn't listed.

Thanks.

---

### Post by jvc26 on 2007-01-24
It should be this I think:
```

sudo dpkg -r avast4workstation_1.0.6-2_i386.deb

```
Il

---

### Post by Kemik88 on 2007-01-24
> dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

I tried a search (using the GUI) for avast in the filesystem but it couldn't find anything.

I tried sudo dpkg -r avast4workstation and that worked. I then removed the avast.desktop from the /usr/share/applications folder to get rid of the link in the menu.

---

### Post by canclan on 2008-04-15
> **Kemik88 said:**
> I tried a search (using the GUI) for avast in the filesystem but it couldn't find anything.

I tried sudo dpkg -r avast4workstation and that worked. I then removed the avast.desktop from the /usr/share/applications folder to get rid of the link in the menu.

Thanks Kemik88!  It worked for me too.

---

