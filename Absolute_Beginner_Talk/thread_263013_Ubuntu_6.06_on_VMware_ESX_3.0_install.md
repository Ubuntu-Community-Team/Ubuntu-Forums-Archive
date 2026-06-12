---
title: "Ubuntu 6.06 on VMware ESX 3.0 install"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by chucksel on 2006-09-22
Can anyone tell me which guest OS to pick for Ubuntu from the following wizard options when creating a guest OS for Ubuntu?

SUSE Linux Enterprise Server
SUSE Linux Enterprise Server (64-bit) [experimental]
Open Enterprise Server
Other Linux (64-bit) [experimental]
Other Linux

(there are several Red Hat choices but I'll assume that they are not candidates)

Any other VMware ESX 3.0 install tips for Ubuntu to give me before embarking on this journey? I am completely new to Linux as well as Ubuntu flavor of it.

Chuck

---

### Post by madcow72 on 2006-09-22
What OS are you trying to create a virtual machine for?  I might be a little confused on the question, but if you're trying to create a guest Linux OS using an install disk for say...Solaris, then I guess you may want to choose "Other Linux."  Out of curiousity, why would you want to install Linux as a guest OS inside Linux?

---

### Post by chucksel on 2006-09-22
The Host OS is VMware ESX server v3.0. The guest OS that will run under the VMware host is Ubuntu 6.06 .  Soooo, Ubuntu will be "riding on top of" the VMware as a guest OS.

Chuck

---

### Post by madcow72 on 2006-09-22
Hmmm.  Sorry, I didn't realize that VMWare ESX could act as an OS.  Either way, I'm sure that "Other Linux" should be the correct choice for creating the virtual machine.  I currently use Windows XP as a virtual machine in VMWare Server using Kubuntu 6.06 as my host OS..works great!  The only problem I have is having to re-configure vmware using ```
sudo vmware-config.pl
``` every time I restart the computer.  However, if ESX is your OS, then I doubt you'll have that problem!  If you're installing on a fresh box, then I'd just go for it, you have nothing to lose.  VMWare seems to be very solid software.

BTW:  Good choice on Ubuntu for your Linux flavor.

---

