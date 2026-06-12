---
title: "Compiz package error"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-10-13
When I try to install the package:
```
alex@ubox:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages
```
The same thing occures with compiz-plugins, but the other way arround.
Cheers.

---

### Post by Foudre on 2006-10-13
aie, same thing when i tried it, the whole paradox of dependancies, even if you try to install them all one command line, same error, in fact 3 of them

---

### Post by alex-desktop79 on 2006-10-13
solution? alternatives?

---

### Post by Thav on 2006-10-13
I think that the compiz plugins package depends on another package (cgw or something) that has since been removed when they made the transition over to Beryl. Try the gandalfn blog post, or play around with the new beryl stuff for compiz action.

---

