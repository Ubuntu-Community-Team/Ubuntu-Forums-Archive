---
title: "Ubuntu PPC in PearPC or QEMU"
date: 2005-07-27
forum: Apple PPC Users
---

### Post by Yagisan on 2005-07-27
G'day,

Has anyone been able to sucessfull install Ubuntu PPC in either PearPC or QEMU ? I can't get it to install in either (QEMU won't boot, PearPC hangs). It's driving me nuts, I don't have a mac, but I want to build my packages for powerpc, but I can't do that unless I setup a powerpc build environment, hence I need to install in QEMU or PearPC.

Any help ?

Thank you.

---

### Post by lubod on 2005-08-24
Well I have no experience with PearPC and only a little with QEMU on a Mac running OS X. But I do have both the PowerPC and x86 Hoary running moderately well.

I was under the impression that building binaries gcc allows you to cross-compile on one architecture for another, like when someone wants to compile a kernel for an embedded ARM device while using the x86 port for example. Some switch like -march whatever the target architecture is called.

Is getting a cheap Mac a possibility at all?

[http://cgi.ebay.com.au/Apple-Imac-G3-350-128-meg-6Gb-HDD-modem_W0QQitemZ5234271298QQcategoryZ4607QQrdZ1QQcmdZViewItem](http://cgi.ebay.com.au/Apple-Imac-G3-350-128-meg-6Gb-HDD-modem_W0QQitemZ5234271298QQcategoryZ4607QQrdZ1QQcmdZViewItem)

That one would most likely be an ok basic system for what you want.

Another thought, can the build environment be set up entirely with synaptic on Hoary, or at least with minimal config. file editing? I'm a long time Mac OS user, but I also have a decent amount of experience with OS X and Linux. I'd be willing to give it a shot if the scope of it is such that you could provide some guidance. 

Maybe set you up a ssh-able account with sudo priviledges if I can figure out a good way to make the Dlink DWL-122 cooperate under Hoary. It works mediocre under some versions of OS X, but I haven't set it up with Hoary. Has a Prism 2.5 chipset, 802.11b, uses USB.

P.S. what is the software you are compiling if I may ask?

P.P.S. In case I'm not in the forum, try emailing me:
lubodATapplelinksDOTNOSPAMnet replace all capital letters with @ and .

---

### Post by airbon on 2005-08-31
I read from the PearPC.net forum that any linux with 2.4 kernel will be able to run on PearPC not the 2.6 version kernel.

---

