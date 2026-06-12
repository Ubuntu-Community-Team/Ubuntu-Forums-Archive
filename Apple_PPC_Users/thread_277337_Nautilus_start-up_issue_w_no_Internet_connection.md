---
title: "Nautilus start-up issue w/ no Internet connection"
date: 2006-10-14
forum: Apple PPC Users
---

### Post by blittle on 2006-10-14
Hello, It seems that I cant a "Nautilius won't start" error if I happen to not have internet access connected to my machine.
I am currently running Ubunt 6.06 on a iBook blue and white clamshell. When I was running verison 5, all I had to do was run hwclock to reset the machine's time and Nautilus woud start right again upon restart. Now, since i've upgraded to 6.06, I get a "timestamp too far in the future' error message if I run hwclock.
It seems that either Gnome or Nautilus won't run unless it checks againt Internet time(?) How do set the machine's time so I can prevent this? Sometimes, I just want to write in my living room which does not have a port for Internet access like my bedroom does.

If you need more info from me to help me let me know.

---

### Post by shadie on 2006-10-15
I had this before after resetting the PMU on a powerbook, I reset the time using the date command and re-booted which got me my desktop back.

---

### Post by blittle on 2006-10-15
thank you i think that would be the date --s command?

---

