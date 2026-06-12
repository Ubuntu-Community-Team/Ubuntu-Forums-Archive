---
title: "[SOLVED] synaptics touchpad"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-23
i just downloaded GSynaptics to customize my touch pad . now when i try to launch it  a message comes:
                      
                 GSynaptics couldn't initialize.
                 You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config
                  to use GSynaptics


  I don't know what it means . can someone help me with some guidance on how to get started with GSynaptics.  :confused:


 Thanx in advance.

---

### Post by macogw on 2008-03-23
Open a terminal (Applications -> Accessories -> Terminal) and type in ```
gksu gedit /etc/X11/xorg.conf
``` then in the file that opens scroll to where it says Input Device and the Identifier is "Synaptics Touchpad".  In that section, add a line ```
        Option          "SHMConfig"             "true"
``` then save and exit.  Log out and log back in, then GSynaptics should work.

---

### Post by bhadotia on 2008-03-23
thank you very much. i don't know what that was. but it worked, GSynaptics is working now.thanx.

---

