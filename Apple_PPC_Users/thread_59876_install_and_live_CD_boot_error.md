---
title: "install and live CD boot error"
date: 2005-08-25
forum: Apple PPC Users
---

### Post by fsman on 2005-08-25
I've tried to load ubuntu 5.04 onto my G3 iMac. 233mhz and currently 32mb RAM (awaiting more!).

Anyway, on install and reboot, I get the following error and a hang

Audit(387379827.094:0) initialized
hda @ MDMA, cycletime: 120, accessTim: 75, recTime: 45
hda: Set MDMA time for mode 2, reg: 0x--211526
Request_module: runaway loop modprobe binfmt-0000
Request_module: runaway loop modprobe binfmt-0000
Request_module: runaway loop modprobe binfmt-0000
Request_module: runaway loop modprobe binfmt-0000
Request_module: runaway loop modprobe binfmt-0000

Any ideas how to get ubuntu CD's to install (note just tried the live CD and I get the same error).

I've no idea what I'm missing here - I've installed on i386 many times with no problems

---

### Post by amohanty on 2005-08-26
I think sometime back this was a deb bug wherein this error is caused due to the kernel being built with 64GB address space support and the hardware not being able to support it.

You could try to provide the following in LILO:
CONFIG_HIGHMEM4G=y

Dunno how to do this with Grub but I am sure some guru here could possibly help out.

HTH
AM

---

