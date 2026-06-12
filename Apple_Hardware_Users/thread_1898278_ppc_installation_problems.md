---
title: "ppc installation problems"
date: 2011-12-21
forum: Apple Hardware Users
---

### Post by mng777777 on 2011-12-21
I am trying to install on my PowerBook g4 and I've run into an issue. The installer cannot find my drive. I upgraded the drive a while back to a Hitachi travel star drive, HTS721010G9AT00. I have formatted the drive. I have searched for a driver for the drive but to no avail. Any ideas?

---

### Post by rsavage on 2011-12-21
What version of ubuntu are you trying to install?

---

### Post by mng777777 on 2011-12-21
11.10 using the minimal CD

---

### Post by rsavage on 2011-12-21
You need to drop to a shell in the installer and "modprobe pata_macio".  If this doesn't work then the easiest thing to do is install 11.04 command line and upgrade.  I wrote a guide [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .  Let us know if the modprobe worked.

---

### Post by mng777777 on 2011-12-22
Thanks for the response. Modrpobe did not work. It returned the response "FATAL: module pata_macio not found."

I will download and attempt with 11.04 instead

---

### Post by mng777777 on 2011-12-22
11.04 found the drive and is about 65% complete installing as I am typing this so it looks like I am all set. Thanks for your help!

---

### Post by rsavage on 2011-12-22
> **mng777777 said:**
> Modrpobe did not work. It returned the response "FATAL: module pata_macio not found."
 
I thought that might be the case. I will amend the instructions accordingly. Thanks for the feedback. I don't suppose you could raise a bug about it? I would do it, but I don't have a functioning powerpc machine at the moment so am reluctant to raise bugs about powerpc. I think the 'linux' package is the one that has the kernel/modules for the debian installer (netboot/mini cd) so that is the package to raise the bug against?

EDIT: I see the kernel team are already aware of this [https://lists.ubuntu.com/archives/kernel-team/2011-November/017979.html](https://lists.ubuntu.com/archives/kernel-team/2011-November/017979.html) , but if you use another module **you need to raise a bug**.

---

### Post by mng777777 on 2011-12-24
11.04 installs without a hitch however while upgrading I get an error message that man-db failed to install. I cannot submit a bug report because it's reported as a crash. The installation completes but with failures and then system reboots. It starts in the 11.10 GUI asking for my password. After entering it I see the 11.10 background but no GUI, only a terminal window. I'm new to Linux and not sure what to do next?

---

### Post by rsavage on 2011-12-24
That's weird.  I can't see any problems with man-db in launchpad with regards to PowerPC.  What are you trying to install - normal Ubuntu or Xubuntu/lubuntu?  You maybe best asking these sort of questions on one of the general discussion forums. 

If you have to re-install then I would install a command line only 11.04 and upgrade to 11.10.  Then install the GUI using a meta package.  That way you can see what is going wrong better.  It's how I describe to do it in the instructions I gave you.

Don't worry about the pata_macio bug it has been fixed in 12.04 already.

---

### Post by rsavage on 2011-12-24
Just a thought, you don't need to adjust your session?  Click on the cog/star/wrench shaped icon when asked to give your password - as demonstrated here [http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome) .

---

