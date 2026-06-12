---
title: "How to remove default apps"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by xjosie729 on 2007-03-16
There are always some programs that comes when I install a desktop. I switched from ubuntu to xubuntu, and it had many packages that I didn't use. I'd like to remove them, but I can't without removing xubuntu-desktop. I am using synaptic package manager to do this. How can I remove them?

---

### Post by pbaehr on 2007-03-16
I believe xubuntu-desktop is a meta-package. (I know ubuntu-desktop is and I'll assume it's the same story)

This means that it's really just an umbrella package that installs lots of other packages, but has no content of it's own. So removing xubuntu-desktop won't actually remove your xubuntu desktop install, just the meta package.

In other words, removing it shouldn't break anything as far as I know.

EDIT: I just checked, it's definitely a meta-package. You can allow it to be removed safely.

---

### Post by Songwind on 2007-03-16
> **pbaehr said:**
> I believe xubuntu-desktop is a meta-package. (I know ubuntu-desktop is and I'll assume it's the same story)

This means that it's really just an umbrella package that installs lots of other packages, but has no content of it's own. So removing xubuntu-desktop won't actually remove your xubuntu desktop install, just the meta package.

In other words, removing it shouldn't break anything as far as I know.

EDIT: I just checked, it's definitely a meta-package. You can allow it to be removed safely.

I think that a sticky with this information needs to be added.  I'm constantly seeing messages where someone thinks they can't remove ubuntu-desktop without removing their whole desktop, and sometimes even in answers to questions.

---

