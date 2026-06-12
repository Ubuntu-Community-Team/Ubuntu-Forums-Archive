---
title: "floppy drive seek failure"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-03-28
Hi everyone, just a quick one.
I installed a couple of extra mem cards the other day, as well as a new CMOS battery, and since then I've been getting this error on startup>  floppy drive seek failure
> f1 to continue or f2 to enter setup so naturally I went into set up and saw that number one was > USB floppy drive but had (not present) beside it.
the options said I could use the space bar to make this 'not bootable'.
Did that.
Next startup same thing so I moved it down to number 5.
Just started up again and same deal. The settings show that this is at number 5 and 'not bootable' yet it stills hangs at this error.
Yes, f1 will continue on through the startup and everything runs just fine.
I don't have a usb floppy drive but in case, for some strange reason, in the future I may need it, I've left the option in there rather than just delete it, which may very well make no difference anyway. 
My concern is that this wasn't happening before and is it a precursor of something more serious in the future?:confused: 
All advice/replies appreciated
Carlos.

---

### Post by kpatz on 2007-03-28
Delete it until you need it.  There's no need to have USB floppy set up in the BIOS unless (a) it's actually connected and (b) you want to *boot* from the floppy.

If you're just using it for data transfer, there's no need to have it set up in the BIOS at all.  The OS will detect the drive when it's connected.

---

### Post by carloslosgrande on 2007-03-28
Ok, will do, thanks Kplatz.
These forums are really terrific.

---

### Post by carloslosgrande on 2007-03-30
Deleted the floppy option from BIOS completely but still getting the error message at startup!?:confused: 
This seems really wierd. Maybe I'll have to do a total reinstall?
Any ideas?
Thanks.

---

### Post by carloslosgrande on 2007-04-08
OK, I found the problem and solution.
In **BIOS** under **Drives - Diskette Drive**
there are several options; OFF    USB     INTERNAL     READ ONLY
the default was INTERNAL so I changed it to USB
and now everything is hunky-dory.

---

