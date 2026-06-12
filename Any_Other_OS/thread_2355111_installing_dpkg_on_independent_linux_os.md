---
title: "installing dpkg on independent linux os"
date: 2017-03-09
forum: Any Other OS
---

### Post by m-al-jayyousi on 2017-03-09
Hi,
I'm planning to make a new linux distro from scratch in the near future, and I am going to use dpkg as a package manager. Does that makes my distro (Debian based) or remains independent?

---

### Post by Frogs Hair on 2017-03-09
It makes package management Debian based.

[https://en.wikipedia.org/wiki/Dpkg](https://en.wikipedia.org/wiki/Dpkg)

---

### Post by m-al-jayyousi on 2017-03-10
Sorry, but I mean if this makes the distro debian based, not the package management.

---

### Post by Frogs Hair on 2017-03-10
You would be using Debian packages/repositories to build the system unless you plan to build all your own packages and create a repository. Another option is RPM which is listed in the see also on the wiki page linked. I'm not sure that you would want to reinvent wheel by building everything from scratch.

---

