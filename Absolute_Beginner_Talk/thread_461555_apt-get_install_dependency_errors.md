---
title: "apt-get install dependency errors"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by RichC on 2007-06-01
Several times when trying various **apt-get install**'s, I get the following type of error:

Depends: libgnomeui-0 (=2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is to be installed

It looks like the package to be installed depends on an older version of the package that is already installed. I could try an '**apt-get install <existing package>=olderversion**' (downgrade), but I'm afraid that might break dependencies of other existing packages and cause them to be removed.

Am I missing a general (safe) work around for this type of error?

Thanks for any help,
Rich

---

### Post by yabbadabbadont on 2007-06-01
Uninstall whichever package depends upon 2.14.1-0ubuntu2.

---

