---
title: "Shutdown causes reboot"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by anoopengineer on 2007-12-14
Hi all,
I am facing a strange problem after I installed Gutsy. 
Every method to shutdown my pc :
*shutdown -h now
*halt
*gnome -> shutdown

all are causing the pc to restart. It shutdowns fine and then reboots! (similar to reboot command)
Then I have to press the power switch manually as the system boots up to stop.

My system is having a mercury motherboard with i845 video chipset, 640MB RAM and two hard disks or 40GB and 80GB.

I have searched the web and this forums, but nobody seems to have faced a similar problem. 
Can anyone help me out from this really annoying issue?

---

### Post by arochester on 2007-12-14
Do you put in :sudo ?

Try: sudo halt now

---

### Post by anoopengineer on 2007-12-14
I have already tried that. no use. feeling a bit desperate now :(

---

### Post by bigken on 2007-12-14
check your bios see if there are any setting like boot from lan ect

if there is disable them

---

### Post by philinux on 2007-12-14
While there check the bios power management settings too.

---

### Post by Sef on 2007-12-14
> While there check the bios power management settings too.

Yes, do that.  I had the opposite problem (reboot = shutdown), and changing a power management setting fixed it.

---

### Post by murphyb on 2008-04-29
I have the same problem.  Shutdown always results in a reboot.  I have checked bios and I can't find any power or boot options set incorrectly.

---

### Post by murphyb on 2008-04-29
Upgraded to 8.04 and problem was solved.

---

