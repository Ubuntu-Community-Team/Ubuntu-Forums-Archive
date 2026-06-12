---
title: "Ubuntu and Dlink DWI-510?"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by greigmg on 2005-09-30
Hi, I'm considering using Ubuntu for a NFS box I'm building, but am worried about this my wireless card.  I've got a dlink DWI-510 PCI wireless-g card and on dlink's support site they don't have any drivers for it.
Is this an absolute bar to using it, or is there some other way (e.g. the OS has built-in support, or a third party has created some workaround)?  As you can tell I'm a complete noob.  Thanks,
Matthew

---

### Post by nitricacid on 2005-09-30
[QUOTE=greigmg]...or is there some other way (e.g. the OS has built-in support, or a third party has created some workaround)?  As you can tell I'm a complete noob.  Thanks,
Matthew[/QUOTE]

I am pretty sure it should have built-in support or atleast a 3rd party program.
I am using a microsoft (wired) router for my network and that works fine and we know MS don't have no support for linux.

---

### Post by poofyhairguy on 2005-09-30
For every wireless device that lacks a Linux driver, you can use Ndiswrapper to force the Windows driver to work in Linux. Its kinda nerdy to do, but thats teh price of admission:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

