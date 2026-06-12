---
title: "deb returns command not found"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-03-28
What do I do to get deb to run?

ratliff

---

### Post by johnc4510 on 2007-03-28
You have to install it.
Right click on the deb package
Choose Open with GDebi Package Installer
When it opens click on install and it should take care of the installation.

---

### Post by lloyd_b on 2007-03-28
AFAIK, there is no "deb" *command*. ".deb" is a package file type.

Could you tell us exactly what it is you're trying to do?  Most likely the answer will involve the "dpkg" or "apt-get" command, but without more information it's hard to help you.

Lloyd B.

---

### Post by crispy_420 on 2007-03-28
Did you try just double clicking the deb file? That has always worked for me. When prompted just type your password.

For the command line it would something like this:

sudo dpkg -i <packagename>.deb
type password
agree (y)

---

### Post by johnc4510 on 2007-03-28
gosh, 3 Tucson people in a row. Never seen that here before.

---

### Post by crispy_420 on 2007-03-29
Must all get off work at the same time.

---

