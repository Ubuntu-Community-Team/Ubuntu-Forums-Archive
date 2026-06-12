---
title: "Stopping on &quot;Starting Up&quot;"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-02-12
I am running Edubuntu, but it is not a server or anything, just standalone, so I think its the same as Ubuntu.  It was running fine for a few days and I made no modifications other than installing the updates, and multimedia packages such as flash and java.

When I power on my computer, it runs the memory tests, detects drives, the hangs on a black screen that says "Starting Up..."

I have read some places to try and hit Ctrl+Alt+F1 while booting, but this hasn't worked.
I have pressed escape while the grub is loading and tried loading into recovery mode with the same result.

Any help would be great!  I am assuming it is going to take some commands in the grub loader screen thing since that is the only place I can type anything.  Thanks.

---

### Post by Herman on 2008-02-12
Did you get a new kernel in your updates?
Have you tried scrolling down in your GRUB menu and booting the older kernel?

If you want to, you can experiment with your GRUB boot loader. The best way to do that is to use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

Regards, Herman :)

---

### Post by TJCIB on 2008-02-13
Thanks for the reply.

I only have the one kernel, the recovery mode, and the memtest in the grub menu.

Is there a command I can insert that will display what is being loaded and therefore let me know what is causing the eternal hang?

The hard drive has been formatted a lot (probably 6 or 8 times), could that be causing it?

---

### Post by Herman on 2008-02-13
I don't think it matters how many times we partition our drives and create new file systems. I have done a lot of repartitioning and making file systems in some of my hard drives and it doesn't seem to hurt them at all.

> Is there a command I can insert that will display what is being loaded and therefore let me know what is causing the eternal hang?
There's another thread that I happen to know of where someone else has a problem that may be similar, and it looks like 'rkd' has a some good ideas about how to investigate the problem, take a look in this thread, [It was all going so well.... 2.6.20-16-generic boot problem]("http://ubuntuforums.org/showthread.php?t=694976")

Regards, Herman   :)

---

### Post by littletinman on 2008-02-13
Yeah, i have that problem too. But i found by pressing the power button once (not held for long time) then it continues with the boot process and i have no more problems.

---

### Post by Herman on 2008-02-13
To make sure it's not a GRUB problem, you should try booting up with [Super Grub Disk]("http://sgd.benjamin-butschko.de/")
Make sure you try to do a 'Direct Boot', because that will bypass the most potential problems in your own installed operating system's GRUB. 
That will maximize your chances of a successful boot.
If it boots okay then most likely you have a GRUB problems and we can try to find out what that is and fix it.
If it still doesn't boot then it's most likely and operating system problem of some kind.  
You can either use Super Grub Disk menus to do that or press 'c' and use the command line, whichever you prefer.

You could also try a file system check.
[                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method, or  [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line

It's probably wise to start with simplest and easiest things first before moving to the more complex and advanced tests and procedures. I should have mentioned these things sooner.

Regards, Herman   :smile:

---

