---
title: "Is there an Ubuntu installation guide for MacBook Air 7,2?"
date: 2015-10-02
forum: Apple Hardware Users
---

### Post by utku2 on 2015-10-02
I have found the installation guide [for MacBook Air 6,2]("https://help.ubuntu.com/community/MacBookAir6-2/Trusty") but not for 7,2. My questions are:

1) Will this work for 7,2 too?

 1.1) If yes, does this create single or dual boot?

  1.1.1) If single boot, do I have to back up OS X before installation? (I have heard that there is a reserved partition for "disaster" cases which can download OS X via internet, in  case one has to install OS X again)
  1.1.2) If dual boot, is there a way to create single boot?
 
 1.2) If no, how can I install Ubuntu 14.04 on MacBook Air 7,2?

Thank you for your time.

Regards

---

### Post by buzzingrobot on 2015-10-02
It's been some time since I tried putting Linux on a MacBook, so with that in mind, my advice is to keep looking for a reliable guide to putting Ubuntu on your specific machine.

If the hardware in the 7,2 is the same as in the 6,2, then I'd think that post could be followed. However, subtle and unsubtle differences often exist between different iterations of the same Apple product. 

OS X creates a "hidden" partition that holds enough code to allow the user to boot into it and restore OS X via an internet connection. If that partition is deleted you'll need the DVD's to re-install OS X.

Dual boot is do-able, but it requires a different approach and different software than dual-booting Windows.

Single booting will happen, of course, if Linux is the only OS on the machine, or if the bootloader is configured to ignore OS X.

I'd suggest keeping an active OS X partition (perhaps shrinking it) and dual-booting.  This will allow you to install future firmware updates from Apple.

---

### Post by utku2 on 2015-10-02
Thanks. By the way, is there any possibility of me somehow screwing up and deleting that "hidden" partition on OS X, or is it simply impossible? If possible, how can it be done so that I will be extra careful not to delete it?

---

### Post by utku2 on 2015-10-02
By the way, my main reason for planning to install Linux is to learn the Linux command line? If I use Linux (and the command line in it) via a VM, would it have any difference using it on a native Linux or would they be completely the same?

---

### Post by wmoore on 2015-10-03
Have you seen the [guide for the Macbook Air 6,2]("https://help.ubuntu.com/community/MacBookAir6-2/Trusty")? I'm not sure what the differences are with the newer model but this might be a good start.

Regarding destroying the Apple partitions .... I did that! But the Macbook will just boot recovery directly from the net, so it's not as big a deal as you think.

---

### Post by Tenn1518 on 2015-10-05
Running Linux on a virtual machine shouldn't have any big problems. The only things that will really be effected is performance. Mostly everything should work, since virtual machines are just machines run inside machines, so Linux thinks it's running natively.

---

