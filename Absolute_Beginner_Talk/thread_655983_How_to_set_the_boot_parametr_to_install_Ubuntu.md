---
title: "How to set the boot parametr to install Ubuntu?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Clarke on 2008-01-02
Hi all, in this guide
[https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45](https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45) its written:
"Gutsy install works with boot parameter "acpi=off". "
How to set this parametr?
Thanks.

---

### Post by dcstar on 2008-01-02
> **Clarke said:**
> Hi all, in this guide
[https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45](https://wiki.ubuntu.com/LaptopTestingTeam/SamsungQ45) its written:
"Gutsy install works with boot parameter "acpi=off". "
How to set this parametr?
Thanks.

When the Live CD boot screen menu appears, you have to press "e" (for edit) and add that string to the end of the default Grub boot string.

You then boot off that selection.

---

### Post by nick_h on 2008-01-02
To make such changes permanent you will need to edit your grub configuration file.
```
gksudo gedit /boot/grub/menu.lst
```

Then add your option to the line starting "# defoptions="
You may also want to add it to the line starting "# altoptions=" (used for recovery mode)

In this way, when the configuration file is updated, such as when a new kernel is added, your changes will not be lost.

---

