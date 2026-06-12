---
title: "password problem"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by pandrew3 on 2005-09-30
Hi,
i had installed the distro about 6 weeks ago and found it to be an easy install in comparrison to say FreeBSB in 1998.  I teach Windows and Apple OSes so i have to keep current with those OSes.
About 2 weeks ago i got the inevitable Windows crash problems and had to spend the next 2 weeks getting the system to work again.
I looked forward to going back and using Ubuntu and did so last night.  **I cannot get into the OS!**  It will not accept my username and password.  I keep a standard Username and password for low security situations as i can have 30+ PC's that i am working on, hence the standard username and pasword.
I am at the login screen and cannot go any further.  I tried to reload Ubuntu but the distro said it could not do that.  I cannot remember how to uninstall.  If it was a Windows OS i have all the appropiate software to change the login.
any suggestions on how i can get around this problem?
1. fix username
2. fix password
3. uninstall (so i can reinstall)
PeterA:confused:

---

### Post by Emerzen on 2005-09-30
Here's what the Ubuntu Guide has to say about this problem:

[http://www.ubuntuguide.org/#changerootpasswordforgotten](http://www.ubuntuguide.org/#changerootpasswordforgotten)

I've seen other's w/ this problem and I know it's an easy fix but I don't know it off hand.  I'll look around and see what I come up w/though.

---

### Post by Emerzen on 2005-09-30
I forgot to mention, I believe you need to boot into the option of your kernel that has (rescue mode) next to it for this to work.

---

### Post by pandrew3 on 2005-10-02
thanks for the reply.  This distro is fighting me all the way.  I could change the password for the root but not the username.  Checked the installation and found an install error.  After re-partioning I started at the beging again but problems. I got the following errors:
madprobe.FATAL: error inserting pciehp./lib/modules/2.6.8.1-3.386/kernel/driver ps/pci/hotplug/pciehp.ko
and the same path for shpchs which was the 2nd madprobe FATAL error.
it got better!  Grub failed to install. lilo failed then the system stopped!  Had to reset the system to start and what happens?  Grub now has an error and XP is not available.  finally got Grub to install and go back into Windows, no Mouse!  not a problem as i teach my students how to navigate without one but very slow.  found the mouse problem. USB hub (4 moths old) is now dead!!
So I have to look at the install problem now.  I assume that i may have selected the wrong distro installation as there were 4 kernels offered.  Which one?  time to do some more reading and searching the net.  I really do like Macs. And my Newton.  That should be a bit of a stir.  Just remember us Aussies have a weird sense of humour (and spelling).
Can i check the /var/log/ messages even though the kernel hasn't installed?  What is the virtual console 3?
peterA

---

### Post by Emerzen on 2005-10-02
Pandrew, not sure what's going on there and I'm sorry to hear you're having such a hard go at it.  Are you installing on a Mac?  If so, you definately have the wrong install CD's.  The 386/586, x86 etc... are for intel/AMD architecture.  If you have an Apple, you need the install CD's for PPC architecture.  If you are installing on intel/AMD, could you post some system info and what install CD/ISOs you have?

---

