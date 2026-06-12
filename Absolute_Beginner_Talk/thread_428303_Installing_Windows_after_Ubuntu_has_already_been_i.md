---
title: "Installing Windows after Ubuntu has already been installed"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by j.miller565 on 2007-04-30
Hi everyone, I just want to know if it is possible to install Windows even though Ubuntu has been installed first.
Thanks

---

### Post by Feba on 2007-04-30
I believe so, but windows might try to over write ubuntu. The easiest path would probably be back everything up, format, and dual boot the normal way.

---

### Post by Pobega on 2007-04-30
Yes, it definitely can, but it's much easier to install Windows first.

Either way, do the partitioning inside of the Windows installer (I'm not sure if it can resize ext3 though, so you may want to do that from a LiveCD and leave free space (Fat?) for Windows), and everything should go normally. When Windows is installed to it's own partition, jump right into the Ubuntu LiveCD and run grub-install (Read the man page for more info) to put GRUB back on the boot record.

---

### Post by mikewhatever on 2007-04-30
Windows will not overwrite Ubuntu since they are on separate partitions. You'll need to reinstall Grub boot loader from the live cd following this how-to
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by j.miller565 on 2007-04-30
Thanks for the help :) Hope it goes all right when I do it. I'll tell you how it goes

---

### Post by blackdalek on 2007-05-03
I have used the command line method described in the link in mikewhatever's post, and this worked for me, no problem.

---

