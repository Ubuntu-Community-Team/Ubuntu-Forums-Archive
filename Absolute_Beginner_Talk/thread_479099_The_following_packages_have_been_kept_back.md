---
title: "The following packages have been kept back"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by wonk-o-matic on 2007-06-20
"The following packages have been kept back"

This message usually means that there's a dependency that can't be met, or that an installed package has a new dependency.  Now, if there's just a new dependency, I can just apt-get install the package.  (If that isn't true, please enlighten me.)  

But how do I figure out that a new dependency is the reason for the message?  I think that there's a package changelog, but I'm unsure where to find it and how to use it.  

Anyone know?

---

### Post by Bachstelze on 2007-06-20
Run *apt-get dist-upgrade* instead of just *apt-get upgrade*. It will install all the dependencies required to upgrade all your packages.

---

