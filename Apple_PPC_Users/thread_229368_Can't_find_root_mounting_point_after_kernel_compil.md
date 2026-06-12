---
title: "Can't find root mounting point after kernel compile"
date: 2006-08-04
forum: Apple PPC Users
---

### Post by bastupungen on 2006-08-04
Hello!
I just made a custom kernel with the help of this guide: 
[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657) (and also the guide suggested later in the thread that uses fakeroot instead of root)
But i am having some problems with loading ubuntu after applying the new kernel

I get the kernel to compile and it installs the .deb's without error. I edit my yaboot.conf and do an ybin -v too. When i restart i can se the "new" kernel in yaboot by tabbing. 

When i load the "new" configuration the kernel seems to be loading fine until i get to the point where it want's to mount the root file system. the "ok" does not appear and waiting for root mounting point appears. After a longer while a shell appears that says /dev/hda3 cannot be found. (/dev/hda3 is where the root file system is located with the older kernel) I also cannot write anything in this shell.

Have i forgotten to do something or is there maybe an fix for this somewhere?

---

### Post by rasec on 2006-08-04
I think there was a thread like this one a couple of days ago, and the person had the exact same problem as you. Anyway, the ubuntu kernel config will not work with the stock kernels. You need to use pmac32_defconfig from arch/powerpc/configs as your base, then you can add/remove options as you please. You may want to specify ext3 and/or reiserfs, depending what type of fs you are using for your root directory. 

Here's my little disclaimer regarding kernels: unless you have a really good reason to a new kernel, stick to ubuntu's. I been there with my powerbook and it was not worth it. Most, if not all, of the latest driver fixes are backported to the ubuntu kernel.

---

