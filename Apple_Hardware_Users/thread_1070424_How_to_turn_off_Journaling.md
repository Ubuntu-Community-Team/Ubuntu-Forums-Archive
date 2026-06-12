---
title: "How to turn off Journaling ?"
date: 2009-02-15
forum: Apple Hardware Users
---

### Post by stevebush on 2009-02-15
I want to turn off Journaling in my OS X volume. How do I trun it off ?

Note: I cannot load the OS as its corrupted and I have to repair it. The install DVD also does not allow this. So Linux is the only way.

---

### Post by pxwpxw on 2009-02-15
> **stevebush said:**
> I want to turn off Journaling in my OS X volume. How do I trun it off ?

Note: I cannot load the OS as its corrupted and I have to repair it. The install DVD also does not allow this. So Linux is the only way.

I think you can open a terminal from the menu bar utilities in the OSX install DVD
If so - (extract form manual ) -
```

diskutil(8) 

     enableJournal device
                Enable journaling on an HFS+ volume.  This works whether or
                not the volume is currently mounted (the volume is temporarily
                mounted if necessary).  Ownership of the affected disk is
                required.

     disableJournal [force] device
                Disable journaling on an HFS+ volume.  This normally works
                whether or not the volume is currently mounted (the volume is
                temporarily mounted if necessary).  If the force option is
                specified, then journaling is disabled directly on disk; in
                this case, the volume must not be mounted.  Ownership of the
                affected disk is required.

```

If you already tried that, I don't know any non-destructive way to disable from linux.

---

### Post by stevebush on 2009-02-15
Thanks. Problem solved.

---

