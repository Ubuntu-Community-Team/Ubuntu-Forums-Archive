---
title: "Why would I have a /boot and  /usr partition?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by willie_wang on 2007-11-29
Silly noob question I know, but I want to understand what the advantages are. I've seen many people suggest it around the web.

Thanks! :)

---

### Post by civic_si on 2007-11-29
/boot is important. that is used at the beginning of the drive where the kernel is loaded from and some use /usr as a separate partition to install software on for multiple reasons.

---

### Post by willie_wang on 2007-11-29
so would it provide any performance increase if I installed ubuntu with a separate /boot partition at the beginning of my drive? if so, how big would I have to make it?

thanks for your speedy reply civic_si :)

---

### Post by civic_si on 2007-11-29
> **willie_wang said:**
> so would it provide any performance increase if I installed ubuntu with a separate /boot partition at the beginning of my drive? if so, how big would I have to make it?

thanks for your speedy reply civic_si :)

I use a 200MB boot partition that is plenty. just after time you will have to clean out old kernels. There would be no performance increase really it is put at the beginning for a certain reason with has eluded me for some reason. If you have Ubuntu make the boot partition it usually makes it somewhere around 200MB.

---

### Post by willie_wang on 2007-11-29
thanks!

---

### Post by aysiu on 2007-11-29
> **willie_wang said:**
> Silly noob question I know, but I want to understand what the advantages are. I've seen many people suggest it around the web.

Thanks! :)
Unless you're running a web server, I don't know why you would need a separate /boot or /usr partition.

A separate /home partition can come in handy, though, if you want to do a clean reinstall and keep your settings and personal files intact.

---

### Post by poudin on 2007-11-29
seperate /var partition can be important, depending on the application...just in case your logging goes haywire..it won't fill up the entire disk and keep the system from loading.

---

### Post by rsambuca on 2007-11-29
There is really no reason for a regular desktop user to have separate /boot and /usr partitions.  Keep it simple to rid yourself of unnecessary maintenance and hassles later on down the road.

---

### Post by aysiu on 2007-11-29
> **poudin said:**
> seperate /var partition can be important, depending on the application...just in case your logging goes haywire..it won't fill up the entire disk and keep the system from loading.
I'm not sure that's a likely scenario, but even if it happens, can't you use a live CD to mount the /var partition and delete any problematic files?

---

