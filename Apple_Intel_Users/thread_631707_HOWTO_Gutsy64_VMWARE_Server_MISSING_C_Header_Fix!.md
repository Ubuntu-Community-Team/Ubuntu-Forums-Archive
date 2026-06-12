---
title: "HOWTO: Gutsy64 VMWARE Server *MISSING C Header Fix!"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by orbstra on 2007-12-04
when installing VMware server on my MBP 15" Core2Duo, I was constantly stopped when installing VMware server because it could not find my current headers folder. It kept defaulting to /usr/src/linux/include when it should have been going to /lib/modules/2.6.22-14-generic/build. (replace 2.6.22-14-generic-build) with your uname -r). It kept telling me that the correct directory nor the default directory did not contain the files or did not exist. I did 2 things to fix this (either may work):
1) I went to [http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html](http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html) and followed those instructions (I beleive this did the trick)
2) I reinstalled (through synaptic) linux-headers-generic, linux-headers-2.6.22-14-generic, and linux-headers-2.6.22-14. I also installed linux-libc-dev (which is for development so it installs this to your /usr/src folder).

I spent alot of time trying to fix that error, and those two methods seemed to do the trick (after hours of research).

enjoy vmware!

---

