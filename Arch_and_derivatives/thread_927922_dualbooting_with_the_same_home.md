---
title: "dualbooting with the same /home"
date: 2008-09-23
forum: Arch and derivatives
---

### Post by dijxtra on 2008-09-23
Has anybody tried dualbooting Arch and Ubuntu using same /home partition? Is it doable?

---

### Post by fwojciec on 2008-09-23
> **dijxtra said:**
> Has anybody tried dualbooting Arch and Ubuntu using same /home partition? Is it doable?

It'd doable, but I'd advise you not to have the same user in both distros -- you most likely don't want to have a single set of configuration files for both distros, since it's a major PITA and results in a lot of weird, unpredictable behavior.

A better solution is to have separate home directories for each distro, and then an additional partition where you store the data that's to be accessible from both distros.  It's a much more elegant solution, and you can link stuff from this "data" partition to the home directories in each distro if you want.

---

### Post by dijxtra on 2008-09-23
> **fwojciec said:**
> A better solution is to have separate home directories for each distro, and then an additional partition where you store the data that's to be accessible from both distros.  It's a much more elegant solution, and you can link stuff from this "data" partition to the home directories in each distro if you want.
Yes, I've been thinking and since Arch uses KDEmod and not vanilla KDE, that probably would end up in a mess. Separate /data partition and then linking seems good enough.

---

