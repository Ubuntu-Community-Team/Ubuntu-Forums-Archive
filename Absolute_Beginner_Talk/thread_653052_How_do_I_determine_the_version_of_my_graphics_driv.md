---
title: "How do I determine the version of my graphics driver?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by WaySensei on 2007-12-29
I'd like to know how to determine the current version of the graphics driver for my ATI Radeon X1600. How can I check this? I appreciate the community's help in baby-sitting me these past few weeks during my first Ubuntu install :D

---

### Post by Perfect Storm on 2007-12-29
There's a little cool application called sysinfo - which display all the stuff you need. It's in synaptic.

---

### Post by WaySensei on 2007-12-29
This program only gives hardware info...it doesn't show the version of my video driver.

---

### Post by p_quarles on 2007-12-29
Try this:
```
cat /etc/X11/xorg.conf | grep -A 3 Boardname
```
The last line should be the driver's name. If not, you'll still find it somewhere in that file.

---

### Post by Perfect Storm on 2007-12-29
> **WaySensei said:**
> This program only gives hardware info...it doesn't show the version of my video driver.

Strange, it do with mine :confused:

---

### Post by WaySensei on 2007-12-29
What finally worked for me was much simpler: I typed 
```
fglrxinfo
```
into the terminal.

---

