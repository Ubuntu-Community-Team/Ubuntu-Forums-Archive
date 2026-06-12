---
title: "Synaptic Error"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bigdawg72987 on 2008-03-08
I am running synaptic to get updates and one package errors out.  It gives me the message
E: /var/cache/apt/archives/sysvinit-utils_2.86.ds1-38_i386.deb: trying to overwrite `/usr/share/man/man1/mesg.1.gz', which is also in package sysvutils

Can anyone help me here?

---

### Post by glennric on 2008-03-08
Where did you get that deb?  The error you are getting is being caused by the fact that the deb you are trying to install conflicts with the packages sysvutils.

---

### Post by bigdawg72987 on 2008-03-08
I am using synaptic/update manager, which ever one floats your boat.  Update manager tells me I need to install updates.  One of the listed updates is sysvinit with its required companion (dependency??) sysvinit-utils, when the package manager attempts to install them, I get the error ^^^^^^ that you see in the first post.

---

