---
title: "What's the difference between Ubuntu kernel and 'plain' kernel from kernel.org?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by john_brown_jr on 2007-03-13
Hi all,

I'm slightly confused about Ubuntu (also SUSE, etc) specific kernels. Why can't we use regular kernels from kernel.org?

Thank you in advance,
John

---

### Post by dstew on 2007-03-13
There is no such thing as an Ubuntu kernel, really. Ubuntu is an operating system distribution that includes a linux kernel, modules to operate hardware, a windows-manager system, a graphical user interface, and lots of applications. The kernel is only the backbone of an operating system; Ubuntu is the full-grown beast. Of course, there are many other species in the jungle...

---

### Post by john_brown_jr on 2007-03-13
OK, let's rephrase the question :) Where can I find a list of bugfixes/backports/etc, which are included in Ubuntu specific 2.6.20-9 as opposed to 2.6.20?

---

### Post by hrp2171 on 2007-03-13
This will probably answer your first question:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

As I was looking for similar information. :(

---

### Post by Matt Yun on 2007-03-13
> **john_brown_jr said:**
> OK, let's rephrase the question :) Where can I find a list of bugfixes/backports/etc, which are included in Ubuntu specific 2.6.20-9 as opposed to 2.6.20?

You should plow through the [Ubuntu Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel.org").  Ubuntu seems to apply **evms** (for hard-drive volume management) and **ck** (performance) patchsets to the stock kernel; I don't know what other patchsets they use.

[I compiled my own kernel with the evms patch only]("http://ubuntuforums.org/showpost.php?p=1710949&postcount=8"), because the default Ubuntu SMP kernel kept hanging.  I suspect the problem that I was having was due to the ck patchset.  My dual-PIII is now happily running a kernel.org SMP kernel with only the evms patch applied, and its uptime is currently 119 days.

The evms patch is absolutely necessary to run Ubuntu, if you are mounting more than one hard-drive.  Not all distros use EVMS to manage hard-drives, but Ubuntu does.  If you leave this patch out, then you will be unable to mount more than one hard-drive.

---

