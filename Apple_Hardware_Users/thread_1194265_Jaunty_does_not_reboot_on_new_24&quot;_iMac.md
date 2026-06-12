---
title: "Jaunty does not reboot on new 24&quot; iMac"
date: 2009-06-22
forum: Apple Hardware Users
---

### Post by knattlhuber on 2009-06-22
I installed Jaunty (64-bit) single-boot on a new 24" iMac (Type 9,1). The system boots up fine and runs without problems. However, when rebooting the system, the screen turns black but the computer stays on and does not reboot (I waited for about 2 minutes). I always have to switch it off manually and then back on again.
It appears *not* to be a firmware problem as the reboot works fine from an OSX installation disk. The Linux partition is blessed as per instructions in the Ubuntu MacTel Guide. All packages are up to date and I have added the MacTel repos and installed the applesmc-dkms package but still no success with rebooting.
Any suggestions what might be the cause of the problem?

EDIT: I should add that this problem does not occur with a 'proper' shutdown (i.e. without reboot). When rebooting with a log from the command line (shutdown -r now >> shutdown.log 2>&1), no error messages are recorded.

---

### Post by dragonleopardpig on 2009-06-23
I have exactly the same problem with my new 20" iMac. I tried with all other main linux distribution Live CD such as Fedora 11, Suse 11, Knoppix......, None of them works. When come to reboot it just hang before the final flash of reboot. Any idea on this?
Thanks.

---

### Post by hajk on 2009-06-23
This is a known problem that first cropped up with the 2009 Mac Mini. I don't know of any solution for Linux yet, but the rEFIt boot selector has the problem solved as of version 0.13. So, you might do some digging in rEFIt's source files.:P

---

### Post by knattlhuber on 2009-06-23
Oh yeah, found the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343781]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343781")

---

