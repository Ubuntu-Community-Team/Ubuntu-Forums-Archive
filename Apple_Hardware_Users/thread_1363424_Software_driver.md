---
title: "Software driver"
date: 2009-12-24
forum: Apple Hardware Users
---

### Post by fslezak on 2009-12-24
I need a driver for a wireless adapter. Can you point me on?

~~~~~~~~~~~Adapter Details~~~~~~~~~~

WUSB54GC v1.0 from Linksys

~~~~~~~~~~~Computer Details~~~~~~~~

Mac OS X 10.3.9 PPC

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by labinnsw on 2009-12-25
[http://www.linksysbycisco.com/US/en/support/WUSB54GC/download](http://www.linksysbycisco.com/US/en/support/WUSB54GC/download)

This should work with ndiswrapper after extraction.

---

### Post by fslezak on 2009-12-29
Where can I find NdisWrapper for OS X?

P.S. I have FINK

---

### Post by inclusivedisjunction on 2009-12-29
> **fslezak said:**
> Where can I find NdisWrapper for OS X?

There isn't one for Mac OS X, and even if there was, I'd think it'd be a real mess to translate x86 binary code to PPC code in the kernel.

Based on the quick research I just performed, WUSB54GC appears to use the Ralink RT2501USB chipset. Ralink provides a driver for this chipset for Mac OS X, but requires you to agree to their EULA online. You may need to modify a file slightly, based on the instructions found below.

[Driver download page]("http://www.ralinktech.com/license_us.php?n=3&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV4THpBMkwyUnZkMjVzYjJGa01EQXlORGN4TlRNek1TNWtiV2M5UFQxU1ZGVlRRaUJFTnpGM0xURXVNeTR3TGpCZlZVa3RNaTR3TGpBdU1GOHlNREE1WHpFd1h6TXdD")
[Modification instructions]("http://forums.macrumors.com/showthread.php?t=235917")

---

### Post by fslezak on 2010-01-02
I tried the method, and got a kernel panic. Any other ideas?

---

