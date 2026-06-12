---
title: "XServer: failed to start"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by tomos on 2006-06-04
Installed Dapper on my Mac PowerBook ppc.  When I finally restarted, I got this message: "Failed to start the XServer (your graphical interface).  It is likely not set up correctly."  I viewed the XServer output "to diagnose the problem".  I looked at [http://wiki.x.org](http://wiki.x.org) to see if I have the latest version.
Not sure.  I looked in "/var/log/Xorg.0.log" and found:

(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

If there is anything that can be salvaged here, I would be happy to hear it.



TIA
tomos

---

