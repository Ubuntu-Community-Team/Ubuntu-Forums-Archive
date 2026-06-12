---
title: "what's this-------fixme:spoolsv:serv_main (0 (nil))"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Greg Mueller on 2008-01-23
I get this in a terminal run

greg@OB-1:~$  wine "/home/greg/.wine/drive_c/Program Files/Finger Lakes Instrumentation/FLIGrab.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
greg@OB-1:~$ 


What's the_______      fixme:spoolsv:serv_main (0 (nil)) _______      part mean?

---

### Post by Hospadar on 2008-01-23
it's probably the location in the code where the error occurred, either in the wine code or the native code.  I would guess it's not something you can fix, but you could always try fiddling with wine config ("winecfg" from the terminal) and see if you can make anything happen

---

