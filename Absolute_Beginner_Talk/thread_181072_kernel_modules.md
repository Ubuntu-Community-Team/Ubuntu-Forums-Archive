---
title: "kernel modules"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by rpm13 on 2006-05-23
The kernel needs and installs a lot of modules eg for usb theres usbcore uhci and such-like.

Is there some place I can find summaries of what these are -- just like synaptic shows a summary for any package?

---

### Post by xfceslacker on 2006-05-23
If you have the kernel source. Then open up a terminal, cd to the directory, type make xconfig. Hit Option->Show Names on the menu bar. Now find the name you're looking for in the viewport to your right and click on it. Then down at the bottom of the window there will be a description. I hope that helps.

---

### Post by xtacocorex on 2006-05-23
The modinfo [modulename] command tells you information about a given module.

---

### Post by rpm13 on 2006-05-23
Thanks but modinfo gives almost no info!!

# modinfo -d thermal
ACPI Thermal Zone Driver
Now I know that thermal has something to do with acpi
# acpi -t
     Battery 1: discharging, 96%,  remaining
No support for device type: thermal
#

But I dont know anything more!

So as xfceslacker said I should look into the kernel sources I guess

---

