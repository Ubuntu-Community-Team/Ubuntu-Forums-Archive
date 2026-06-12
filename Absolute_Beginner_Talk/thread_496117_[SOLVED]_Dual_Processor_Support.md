---
title: "[SOLVED] Dual Processor Support"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by jeffrla on 2007-07-08
Hi all,

I am running a Dell PowerEdge 2500 Server with two 1.13GHz processors.  I am running the 2.6.20-16-386 kernel.

Currently, my system is only seeing one of the processors.

What do I need to do to get it to recognize the other processor?

Thanks,

Jeff

---

### Post by Vajra Vrtti on 2007-07-08
Use kernel **2.6.20-16-generic**.

---

### Post by jeffrla on 2007-07-08
Hello,

I install the generic kernel.  It looked like it installed ok.  It said it needed to reboot.  I rebooted, but when it came back up, it was still using the 386 kernel.  Is there something else I need to change to get it to start using the new kernel?

Thanks,

Jeff

---

### Post by jeffrla on 2007-07-08
Hey Chief,

I edited the Menu.lst file and set the Generic kernel as the default and rebooted.  The system came back up and now sees both processors.

Thanks for your help.

Jeff

---

### Post by Vajra Vrtti on 2007-07-08
That's strange. The install process was supposed to update *menu.lst* so that you have the option to chose either kernel at boot time.

---

### Post by jeffrla on 2007-07-08
Hey dude/dude-ett ;-)

Thank you for the quick response.  Not sure what happened. The installed looked good - no errors, etc.

One thing I noticed prior to the mod was that the Flurry ScreenSaver seemed sluggish.  I chalked it up to the 2nd CPU not being used, but even after the 2nd CPU came up, the SS still seems sluggish.

Not sure.

Thanks,

Jeff

---

