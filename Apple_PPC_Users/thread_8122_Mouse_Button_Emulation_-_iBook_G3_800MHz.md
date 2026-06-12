---
title: "Mouse Button Emulation - iBook G3 800MHz"
date: 2004-12-14
forum: Apple PPC Users
---

### Post by Sintara on 2004-12-14
Hi, all.  I'm trying to figure out the mouse button emulation scene on my iBook G3 800MHz, but I'm at a loss.  I read another post dealing with a Wallstreet Powerbook stating that F11 and F12 are mapped to right- and middle-click, but these aren't working on my iBook.  Where is the configuration file for these mappings?  Is there anything I should keep in mind when configuring my mappings?

---

### Post by Sintara on 2004-12-14
I located the config file.  It's at:
     /etc/sysctl.conf
I tried mapping Mouse2 to the Apple Command key, which *showkey* tells me is 0x7d, but that didn't work either.  Anyone have any ideas?

---

