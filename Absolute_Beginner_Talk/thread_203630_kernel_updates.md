---
title: "kernel updates"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by oskie on 2006-06-25
Two questions: 1. Are kernel upgrades essential from a security perspective for a home PC/laptop? 2. If not, how can I download updates for applications etc. without upgrading my kernel in the process? 

The reason why I ask is because I assume that a kernel upgrade means reinstalling my wireless and videocard drivers, which is something I would like to avoid. ;)  Thanks for you help

---

### Post by johnc4510 on 2006-06-25
Well, Security updates are just that, for sercurity. I personally update everything, everytime. You can lock any package to keep it from updating by opening Synaptic, clicking on the app you don't want updated, and then choosing Package, then choose Lock Version. I personally wouldn't do this, but that decision is up to you. Good Luck

---

### Post by catlett on 2006-06-25
kernel updates are not essential. you can unselect them when updating.

The update manager on startup will notify you of any updates in the top right hand corner. When you hit on the icon the updater will open up and give you a list of available updates. Just unselect any kernel updates and they will not be installed.

If you want to experiment, the grub menu will be updated and it will list the new kernel and the old kernel. If you select to boot with the new kernel and it doesn't keep your configuration, you can select the previous kernel from the grub menu next time you boot.  Then you can remove the kernel with Synaptic Package Manager by highlighting it and selecting "mark for removal". Kernels are listed as "kernel-image"s in synaptic.

P.S. Now that you're asking I can't remember but I do not think the kernel will change your configuration. It might not "jive" with the configuration and have problems but you drivers shouldn't be affected by the process.

---

### Post by oskie on 2006-06-25
Thanks for the feedback.

---

### Post by pshnfry on 2006-07-16
Kernel updates break my WiFi drivers - RaLink chip with manufacturers linux driver. fwiw. 2.6.12-10.33. Haven't updated kernel since. Have downloaded Dapper and will upgrade shortly (and I expect revisit the time lost getting wireless working again)

---

### Post by editrix on 2006-07-16
> **catlett said:**
> P.S. Now that you're asking I can't remember but I do not think the kernel will change your configuration. It might not "jive" with the configuration and have problems but you drivers shouldn't be affected by the process.

A kernel update wiped out my modem. I suspect anything that has to do with /kernel/drivers/ or modules could break. And I haven't updated a kernel module since.

---

