---
title: "Radio card not working"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Talon2 on 2006-11-18
I'm trying to get my Radiotrack I card (FM radio) working under Dapper.

Gnomeradio shows this error in a dialog:
---
Could not open device "/dev/radio0" !

Check your Settings and make sure that no other
program is using /dev/radio0.
Make also sure that you have read-access to it.
---

/etc/modules shows this:
---
lp
psmouse
alias radio radio-aimslab
options radio-aimslab io=0x30f
---

I've been googling with no success.  My experience level with linux is not that great at this point.  I have no idea what to look at next.  Any help appreicated.

---

### Post by Talon2 on 2006-11-18
How can I verify the correct module (driver) is loading?

Should the driver creat a file can /dev/radio if it is loading correctly?

---

