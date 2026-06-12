---
title: "k53e can no longer suspend/reboot/shutdown"
date: 2013-02-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Helios747 on 2013-02-10
Hello,

I've recently started using Linux again, and installed xubuntu 12.04 32 bit (various reasons I went with 32 rather than 64 bit) and installed the usual scripts from this blog to fix the suspend problems that have always plagued this laptop.

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

However, this script, and any script I've tried to find on google simply hasn't worked. I can get the laptop to boot fine, but suspend, reboot and even shutdown simply hangs the laptop.


I've tried that script from the link above

I've tried acpi_osi=windows kernel arg

I've tried simply unloading ehci-hcd manually.


Nothing is working anymore.

Attached is every logfile that might be relevant. I really don't want to go back to Win7 on this machine, it's way too slow.

dmesg: [http://pastebin.com/4c0hrrrb](http://pastebin.com/4c0hrrrb)

pm-suspend: [http://pastebin.com/AKWrG0YU](http://pastebin.com/AKWrG0YU)

syslog: attached as tar.gz

I've tried all of this on 3.2.0-37-generic-pae and a vanilla 3.7.6 kernel from kernel.org


HEEELP

---

### Post by Helios747 on 2013-02-11
bump

---

### Post by Helios747 on 2013-02-19
bump

---

### Post by Schnappi1989 on 2013-02-21
sorry to see that no one has solve this problem! :popcorn:

---

### Post by mobo on 2013-02-25
Nothing to offer in the way of assistance but I can't help but wonder why my K53E has zero issues with Ubuntu 12.04 or 12.10.

---

