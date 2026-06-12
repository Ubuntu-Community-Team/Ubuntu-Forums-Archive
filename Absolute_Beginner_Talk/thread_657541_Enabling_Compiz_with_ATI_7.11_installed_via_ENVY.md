---
title: "Enabling Compiz with ATI 7.11 installed via ENVY"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2008-01-03
Hi,

I've installed the 7.11 ATI drivers via ENVY (not using 7.12 because it doesn't support my 1400 x 1050 resolution).

but I can't get compiz enabled.  Here is the output of "Compiz--  Replace"

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Here is the output of "glxinfo | grep direct"

direct rendering: Yes


---
Anyone know what I can do to get compiz working?

I've made sure to add "fglrx" to the compiz whitelist

Thanks.

---

### Post by skymera on 2008-01-03
try

sudo apt-get install xserver-xgl

---

### Post by tepidarium on 2008-01-03
> **skymera said:**
> try

sudo apt-get install xserver-xgl

Cool...that seemed to enable compiz - but I thought the new ati drivers don't need xgl to work that it can use AIGLX?

Can ou tell me the xgl uninstall command if I need to uninstall it?

Thank you again.

---

