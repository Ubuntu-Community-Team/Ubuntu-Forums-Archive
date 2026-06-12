---
title: "If I config-make-install a program, where does it get installed to?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-05-01
The folder I'm currently in (e. g. ~/Desktop/Programname) or some preordained folder such as /usr/bin?
:confused:

---

### Post by Bachstelze on 2007-05-01
Most often, everything goes in the right place : binaries in /usr/bin, libraries in /usr/lib, etc. However, this can usually be overridden with the "prefix" parameter to *configure*. Also, you might want to try *checkinstall*, which will "trace" where the program installs it's files and build a package for it.

---

### Post by Blofeld on 2007-05-01
Many thanks!
I am using checkinstall, it told me it had installed everything to that Desktop folder, that's why I'm asking!

---

