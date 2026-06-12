---
title: "Manually updating trusty powerpc-smp kernel to backported HWE kernel"
date: 2017-02-22
forum: Apple Hardware Users
---

### Post by dsmithhfx on 2017-02-22
Hi,

I'm getting the following message when ssh-ing into a headless 14.04.5 powerpc-smp (32-bit) on G4 hardware:

"WARNING: Security updates for your current Hardware Enablement Stack ended on 2016-08-04"

The unsupported kernel is 4.2.0-42-powerpc-smp ppc

After some investigation, I've learned that I need to upgrade to a 4.4x kernel for continuing HWE support through 2019.

A candidate, linux-image-4.4.0-64-powerpc-smp is available. Will installing this satisfy the HWE requirement going forward?

Will it pull through dependencies, or do I need to also install linux-headers-4.4.0-64 and linux-headers-4.4.0-64-powerpc-smp?

Any reason to suppose doing this would break my server?

Thanks for any advice!

---

### Post by deadflowr on 2017-02-22
*Thread moved to **Apple Hardware Users**.*
I'm not sure on PowerPC and hwe, but maybe one of the many trusted Apple hardware users will.

> Any reason to suppose doing this would break my server?
Not outright, but any kernel upgrade such as these always has the potential to have a hiccup or two.
The preferred situation for servers is to run the original kernel series for LTS releases, 
(unless the hardware is too new to run the original kernel series)
as that kernel is supported for the whole release period.
Thus no need to worry about kernel upgrade hiccups.

---

### Post by dsmithhfx on 2017-02-23
OK thanks. I'll leave it be.

---

