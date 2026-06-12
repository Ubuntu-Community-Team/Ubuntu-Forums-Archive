---
title: "Adding application to stop services list in acpi-support"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by notamonopoly on 2007-06-18
I'm running vmware in feisty and when I come back from hibernation, I get the error "Interface vmnet1 is not marked 'UP'".

I found the solution: "try adding vmware to STOP_SERVICES in /etc/default/acpi-support" but I can't seem to get it to work.

The file "/etc/default/acpi-support" had:
STOP_SERVICES="mysql "

I changed it to: 
STOP_SERVICES="mysql, vmware"

and when that didn't work:

STOP_SERVICES="mysql vmware"

but neither worked. I've done a clean boot after updating the file and it made no difference the next time I came back from hibernation.

Have I edited the file incorrectly? Is there something else I have to do?

This is a minor issue but something I would like to get working.

Thanks

---

### Post by notamonopoly on 2007-06-18
I've found a number of other posts that indicate that it should be separated with a space so I've returned it to:

STOP_SERVICES="mysql vmware"

And still no good.

---

### Post by samosamo on 2007-10-28
This is a good question, can someone answer please ?

---

