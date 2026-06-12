---
title: "acpi-off ok? or bad news?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-11
i have a toshiba and the only way i can get sound is to boot acpi=off. Is this ok to do? Its a bug that wont let me get sounds and from hat i can see its not going to be a fast fix at all. I would like to be able to see my battery state, is this somehow possible do see with acpi=off? what are the pros and cons of booting acpi=off?

thanks in advance!

---

### Post by spupy on 2007-11-11
As far as i know, you should not turn off acpi. It is not only about the battery. I once turned it off by mistake (a toshiba laptop, too) and the computer overheated, because the fans weren't working. 
What is your computer? Maybe we can help with the bug?

---

### Post by skymera on 2007-11-11
well i turned acpi off.

nothing can detect my fans anyway :S

---

### Post by natehatewindows on 2007-11-11
its a toshba p-105 S6187 with a intel hda conexant (vience) chip. sound works fine when i boot acpi=off. here is the bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)


thanks!! :) 

it would be SO COOL to have sound!

---

### Post by spupy on 2007-11-11
> **skymera said:**
> well i turned acpi off.

nothing can detect my fans anyway :S

ACPI doesn't detect my  fans and sensors, too, but without it they don't work at all.

---

### Post by natehatewindows on 2007-11-12
well i tried yesterday to boot acpi=off for a short time, i used as normal compiz and my computer seemed to get more hot that normal so i decided i will not do this again and will wait for god knows how long until there is a fix to this bug. my fans were on all the time but never changed rpms, they were just going real slow and never sped up like they usually do.

---

### Post by spupy on 2007-11-12
Since the bug is in the 2.6.22 kernel, have you tried another kernel? Maybe compiling your  own kernel will help, too.

---

### Post by natehatewindows on 2007-11-12
well i could do that but....yes there is a but i have a linuxant driver for my modem (i only have dial up here in ukraine). i bought the driver so if i do another kernel the driver wont work. any ideas?? and also people who have been using a vanilla kernel have had fan issues.

---

