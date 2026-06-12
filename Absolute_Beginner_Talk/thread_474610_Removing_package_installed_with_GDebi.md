---
title: "Removing package installed with GDebi"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-06-15
I installed a .deb package using GDebi, but it isn't exactly what I need, so I want to remove it - but I can't use Synaptic or Add/remove. I've looked at GDebi, but it doesn't seem to have an uninstall option. How can I do this?

TIA

---

### Post by kevdog on 2007-06-15
If you know the package name try this:

sudo aptitude purge *package_name*

---

### Post by freesitebuilder on 2007-06-15
That worked - thanks!

---

