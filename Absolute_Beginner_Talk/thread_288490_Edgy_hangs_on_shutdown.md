---
title: "Edgy hangs on shutdown"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Jeff294 on 2006-10-29
After upgrading to Edgy from Dapper, my PC now hangs when shutting down from Edgy. I have a dual boot set up, and the PC does NOT hang when leaving Windows. This behavior did not happen under Dapper. When it hangs, it leaves the screen displaying the Ubuntu logo (the circle and the 'ubuntu' letters), and a progress bar showing zero percent. I have to unplug the power cord to get past this. The PC can then be started normally with no problems, in either operating system.

Anybody have any ideas? Any other details that I can provide? 

Thank you for your help!

---

### Post by Jeff294 on 2006-10-30
More information: 
Upon further investigation, I found that Edgy hangs when I do a RESTART, but not when I do a SHUTDOWN.

I found a thread that suggested adding acpi=force to the defoptions line of the /boot/grub/menu.lst - I tried that and it didn't seem to change anything.  

Anybody have any suggestions for what to try next?
Thanks!

---

### Post by paul6 on 2006-11-01
I am having the same problem, except it only hangs on shutdown, not reboot.

When I had Dapper, the "acpi=force" trick fixed it. In Edgy, however, adding this option turns my CPU fan **completely off**.

Any help is appreciated.

---

