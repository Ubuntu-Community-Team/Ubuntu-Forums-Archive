---
title: "Problem: Synaptic Package Manager"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by dhuang on 2007-03-12
when I install package via synaptic package manager, it said "E: liblog4j1.2-java-doc: subprocess post-installation script returned error exit status 2"

---

### Post by jdfreshwater on 2007-03-13
you may need to clean out your apt-get as something may be stuck in it.  At the command line type in   *sudo apt-get autoclean*.   This should hopefully allow you to try and reinstall the package.

---

