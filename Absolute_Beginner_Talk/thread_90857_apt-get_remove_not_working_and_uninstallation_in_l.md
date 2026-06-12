---
title: "apt-get remove not working and uninstallation in linux"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by s0c0 on 2005-11-15
When I use the apt-get remove command or try to remove packages through synaptic the package is not fully removed.

For instance I recently installed apache 2.0 and decided I would remove apache 1.3.  The output looked like it was removing stuff, it verified that I really wanted to remove it, but then it didn't do it!  I still have /usr/lib/apache, /usr/share/apache, and /etc/apache.

How do you actually remove stuff in linux?  Do I just go through and remove all the directories and files associated with a give package?  Please advise.  Thank you.

---

### Post by aysiu on 2005-11-16
[QUOTE=s0c0]When I use the apt-get remove command or try to remove packages through synaptic the package is not fully removed.[/QUOTE] There's an option in Synaptic to mark something for complete removal (include configuration files).

---

