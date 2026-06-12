---
title: "Installing Programs"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by jimwinfrey on 2005-10-07
How do I install programs that are outside the Ubuntu libraries?  apt-get update, upgrade don't find them.  I want to download and install the genealogy program Gramps from the Debian libraries and I can't find instuctions that work.  Looks like they're written one level above where I'm operating at this point.

Thanks,

Jim

---

### Post by nitricacid on 2005-10-07
Ummm... do a search in the Synaptic Package manager.
Search GRAMPS

---

### Post by mlomker on 2005-10-07
> How do I install programs that are outside the Ubuntu libraries?

The safest thing is to download the .deb file and then use this command to install it:

```

sudo dpkg -i packagename.deb

```

It is possible to add a regular debian repository in Synaptic, update, and then it'll show up.  The danger is that it might download a lot of unintended files and damage your system.  Ubuntu and debian are not 100% compatible.

---

