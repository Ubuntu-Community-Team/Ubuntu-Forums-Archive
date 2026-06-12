---
title: "color bars only on G3"
date: 2004-11-12
forum: Apple PPC Users
---

### Post by csccs on 2004-11-12
Obviously my ati card isn't supported.  What now?  I briefly see command lines.  Install sets automatically, then I get a screen full of color bars.  Any thoughts?

---

### Post by sumanjay on 2004-11-13
ATi cards are supported, mostly out of the box. If you can provide some more details about your Mac, like the year and the name, along with some hardware details, we might explore some ways to get X going. Also, post your XF86Config file from the "/etc/X11" directory and your logs from "/var/log/X11". Also need to know if this is happening when you're installing the OS or after you have, when you're trying to log in.

---

### Post by csccs on 2004-11-14
Currently I have os X 10.2.8 running on my G3 version 2.2.  It has a 300 mhz processor, over 300 mg ram, and has an ATY, xclaimvrpro display card.

I put in the linux install disk and the system boots.  I briefly see a command prompt, but then the screen switches to verticle color bar giberish.  I assume this is the gui displayed improperly.

---

### Post by csccs on 2004-11-14
Okay, it now installed.  But upon reboot immediately after:

[Tux picture]
audit(1098310169.241:0): initialized
Starting Ubuntu...
pivot_root: No such file or directory
/sbin/init: 429: cannot open dev/console: No such file
Kernel panic: Attempted to kill init!

Thoughts?

---

### Post by csccs on 2004-11-14
I see this problem has occured before with no clear resolution in other threads.  Did anyone ever find a solution?

---

