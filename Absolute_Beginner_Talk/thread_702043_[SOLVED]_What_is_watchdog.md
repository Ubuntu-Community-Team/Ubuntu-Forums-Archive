---
title: "[SOLVED] What is watchdog ?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-19
I did a 'top' command from terminal, and I noticed there are a few (4-5) processes called '*watchdog*' running, what is that and why are there so many of them running?

---

### Post by y-lee on 2008-02-19
hmmm, nothing to worry about it seems 

> The watchdog program writes to /dev/watchdog every ten seconds. If the device is opened but not written to within a minute, the machine will reboot. This feature is available when the kernel is built with 'software watchdog' support (standard in Debian kernels).



See [Package: watchdog (5.3.1-4)]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4366189") and[ Watchdog The Linux Software Daemon]("http://www.linuxjournal.com/article/217")

---

### Post by BassKozz on 2008-02-19
Thanks y-lee

---

