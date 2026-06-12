---
title: "Feisty Fawn issue on boot s10 acpid"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Paradoxed on 2007-04-02
Good day all,

Have upgraded to Fesity and system hangs on boot. The following errors

/etc/rc2.d/s10 acpid :line 54 : 4357 segementation fault

So had a look at the above

this from line 51 
	if [ -n "$MODULES" ]; then
		log_begin_msg "Loading ACPI modules..."
		STATUS=0
	        for mod in $MODULES; do

Any help appreciated

---

### Post by johnny4north on 2007-04-02
have you ran the cd test for the "live Ubuntu Cd"?  you will see it right when you boot in the live cd. its the 3rd or 4th choice down.  use the down and up arrow the select, then run.  you may have a damaged module or dirty disk.  the other is that ubuntu doesnt like your energy setting in the system bios.  please stay out there, until someone{better then me...} could walk you though..  thanks Ubuntu

---

### Post by Paradoxed on 2007-04-02
> **johnny4north said:**
> have you ran the cd test for the "live Ubuntu Cd"?  you will see it right when you boot in the live cd. its the 3rd or 4th choice down.  use the down and up arrow the select, then run.  you may have a damaged module or dirty disk.  the other is that ubuntu doesnt like your energy setting in the system bios.  please stay out there, until some{better then me...} could walk you though..  thanks Ubuntu


Havent had any issues on 6.10 so doubt that there are any new hardware issues.

---

