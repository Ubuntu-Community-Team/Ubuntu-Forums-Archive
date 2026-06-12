---
title: "Debootstrap error upon install"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by TheCyrus on 2005-12-23
I'm trying to install Ubuntu Breezy on a seperate partition on my x86. I can get past the paritioning, but when it comes time to install the base system. I always get a debootstrap error (with return value 1) about 6-10% or so into installation. It is always at the same point in the installation.

I am using an Ubuntu Breezy Pressed CD.
Any help would be great, someone has already suggested i use
```
linux acpi=off
```
 to no avail.

Can anyone provide any suggestions?

---

### Post by az on 2005-12-23
CTRL-ALT-F3 to see the error screen.  What is the last error (or last few) displayed.

---

### Post by TheCyrus on 2005-12-23
the error is:
```
tar: ./us/share/man/man3/Locale:gettext.3pm.gz: Invalid Argument
```

---

### Post by az on 2005-12-23
I would suspect you have a bum cd.  Woudl you try running an integrity check?

---

### Post by TheCyrus on 2005-12-23
How would I do that?

---

### Post by az on 2005-12-23
Whan you boot it, it will ask you to configure the languange and keyboar.  You can select "Go Back"  (I think that is what it is) and you get shown the complete menu of options.  Pick "Check Cd integrity"

---

