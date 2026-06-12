---
title: "linux-restricted-modules-386"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-01-24
I've got an Intel processor, and I have both
linux-restricted-modules-386 and 
linux-restricted-modules-generic installed

generic was installed initially - I just installed 386 through synaptic.

can I safely mark the linux-restricted-modules-generic for "complete" removal.  If I do, what are the ramifications, if any?

---

### Post by ctswhole on 2008-01-24
If you want to see what would be removed, you can enter this into your terminal:

sudo apt-get -s remove <package-name>

The output should tell you what package(s) and dependencies would be removed without actually removing them yet.

---

