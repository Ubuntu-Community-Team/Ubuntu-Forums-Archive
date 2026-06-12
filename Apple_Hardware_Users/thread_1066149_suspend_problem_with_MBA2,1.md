---
title: "suspend problem with MBA2,1"
date: 2009-02-10
forum: Apple Hardware Users
---

### Post by v3n on 2009-02-10
Hello,

I've managed to install 8.10 on my air2,1 (nvidia graphics)
The main problem is with suspend to ram.
After upgrading gnome power manager from ppa repos, the system suspends OK when I close the lid, but It seems to wake up "by itself", without any action :confused:
It stays in suspend state for a variable amount of time, and I'm not able to guess what triggers the waking up...

Many thanks for any help,

Vincent

---

### Post by hyperboloid on 2009-02-11
I had flaky suspend experience caused by the "sky2" module. I'm told that the MBA is similar hardware to MBP 4,1, so maybe this applies in your case. You can try unloading sky2 module on suspend, by adding the line 
```
SUSPEND_MODULES="sky2"
```
to the file /etc/pm/config.d/00sleep_module. See [this thread]("http://ubuntuforums.org/showthread.php?t=1058687") for further details.

---

### Post by v3n on 2009-02-11
Hi, and thanks for your answer,

BTW, the sky2 module is not loaded in the MBA (no NIC). Checked with lsmod.
By checking dmesg output, the "auto wakeup" issue seems to be related to ACPI:
Before suspending, ohci module says things about "wake up capabilities enabled by acpi", so it seems like default ACPI wakeup options are not OK.

One more detail (I'm not sure about that...): it seems that the waking up is triggered by "shaking" the MBA (quick upside down and back) :confused:

Vincent

---

### Post by v3n on 2009-02-11
Some news:

I'm pretty sure the wakeup event comes from usb.
So, I'll try to blacklist ohci_hcd :P

Vincent

---

### Post by v3n on 2009-02-11
It works!

SUSPEND_MODULES="ohci_hcd"

I know this is a very ugly workaround, but it does the job  :)

Vincent

---

### Post by gwydionwaters on 2009-09-25
would this be the case even if no usb devices were currently plugged in?

---

