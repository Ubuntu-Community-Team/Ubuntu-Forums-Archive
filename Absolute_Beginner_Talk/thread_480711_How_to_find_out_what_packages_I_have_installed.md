---
title: "How to find out what packages I have installed"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Millenniumman on 2007-06-21
How can I find out what packages I have installed (rather than the ones that came with ubuntu)?

---

### Post by Skrynesaver on 2007-06-21
dpkg --get-selections
Or for slightly more detail
dpkg --list

---

### Post by Millenniumman on 2007-06-21
Those show me all the packages installed on my computers. I just want to see the ones *I* have installed, not the ones installed by the installer.

---

### Post by Millenniumman on 2007-06-21
Also, I'd prefer it not to list packages that are already installed by other packages it lists, but it is okay if it does.

---

### Post by caro on 2007-06-21
A quick, easy way to see what you've installed is to open Synaptic and go to File > History.  It will show you what you've loaded by date.

---

### Post by Millenniumman on 2007-06-21
Thanks. That works.

---

