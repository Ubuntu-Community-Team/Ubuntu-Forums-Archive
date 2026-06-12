---
title: "not starting installed ubuntu"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by vinsindia on 2006-05-05
hello i installed ubuntu 5.10 on my pc. but installation did through command
"linux acpi=off". ifter installation it giving only prompt. no graphics as arrow,window, etc.
is this installtion right?
the cd-rom installed all component as open office,xscreensaver,clipboard,etc.
how can i access this for graphics?
plz help
__________________
vinayak aghor

---

### Post by cgjones on 2006-05-05
Does you computer support ACPI? You should be able to check the BIOS to see if it does or not.

To start the graphical environment, log in, then type the following:
```

startx

```

I haven't actually had to do this yet myself, but I believe this should start the X server if it is installed.

---

