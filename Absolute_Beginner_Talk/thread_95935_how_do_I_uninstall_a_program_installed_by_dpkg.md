---
title: "how do I uninstall a program installed by dpkg?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by bailout on 2005-11-27
I installed opera by dpkg on a deb and have since noticed that they have started a repository so opera can be installed and maintained via synaptic.

How do I uninstall the version I installed using dpkg so that I can add the opera rep and use that instead?

---

### Post by Xian on 2005-11-27
Apt knows what you installed with dpkg.
You don't need to uninstall it before you add the repo.

But if you want you can do so right now:

$ sudo apt-get remove opera

---

### Post by ssam on 2005-11-27
you should be able to find it in synaptic and choose which version you want.

---

