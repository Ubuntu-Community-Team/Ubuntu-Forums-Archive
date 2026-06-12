---
title: "no wifi in fedora 16"
date: 2012-02-21
forum: Any Other OS
---

### Post by doppel.ganger on 2012-02-21
Just did a fresh install of Fedora 16 on a HP Mini 5101, and it does not list  wifi or wireless anywhere in the connections icon in the panel. Gnome 3 btw. I do have it connected to ethernet right now and that works nust fine. HELP!!!!

---

### Post by boydrice on 2012-02-21
Hi,

Since you didn't include specific info about what wireless card you are in possession of I did a google search and determined that you must have some sort of Broadcom card.  Subsequent google searches led me to this Fedora Forum How To.  Perhaps this might help.
forums.fedoraforum.org/showthread.php?t=239922

---

### Post by doppel.ganger on 2012-02-21
Ok, lspci says I have a BCM43224, and that chart tells me I need the driver broadcom-wl. Correct?

---

### Post by boydrice on 2012-02-21
> **doppel.ganger said:**
> Ok, lspci says I have a BCM43224, and that chart tells me I need the driver broadcom-wl. Correct?

That is how I read it as well.  Good luck.

---

