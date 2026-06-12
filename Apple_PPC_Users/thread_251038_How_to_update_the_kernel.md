---
title: "How to update the kernel?"
date: 2006-09-04
forum: Apple PPC Users
---

### Post by rscow on 2006-09-04
Hi, all.  I am running a MacBook, and it is set up now for triple booting, with OSX.4.7 and WinXPHome and Ubuntu 6.06.  I am pleased that I got it up and running and am still configuring the Ubuntu side.  The help and inspiration that comes from this community is amazing and really gratifying.

My problem is with wireless access.  I have the 686-SMP kernel.  It is the one with the may 2006 date.  I am in OSX now, so don't have the exact numbers.  What I think I need to do is update the kernel, and also get rid of madwifi and network manager files and install the madwifi-ng and reinstall network manager daemon etc.  

So, how do I update the kernel?  I think the new one is from July. Is it as simple as:
"sudo apt-get install linux-686-smp" followed by the restricted modules ?

Or am I missing something.  After all the work to get Ubuntu up and running, I hate to ruin the installation.

Sorry for the noob question.  I appreciate your help.

Roger

---

### Post by hajk on 2006-09-05
Yes, as simple as that. You might find it easier to use Synaptic.

As to madwifi-ng, those drivers are part of the restricted-modules package --
make sure the version is the same as the kernel. 
Getting the madwifi-ng drivers to work properly with the Atheros chip in the MacBook is an entirely different story... you may need to try several times in the System - Administration - Networking menu to activate this, possibly followed by "sudo ifup ath0" in a terminal. Even then, signal strength may be low, such as 54/94 when next to the wireless access point! Maybe there will be a better version of madwifi-ng soon.

---

### Post by rscow on 2006-09-05
Thanks, Henk.

Actually, I sudo apt-get install linux-686-smp.  It showed that it was already there.  I should do sudo apt-get update linux-686-smp, or the corresponding search in Synaptic (search for 686-smp, right?). Then install.

Should I delete all the madwifi stuff first, and then update the kernel and restricted modules?  

I have visited your site and printed your dual boot .pdf.  I will see what stuff I have missed or screwed up (although Ubuntu does boot and run).  Just want to get wireless up now.  Tired of sitting in my daughter's room using an ether net cable.:-)

Best,

Roger

---

### Post by hajk on 2006-09-05
> **rscow said:**
> Thanks, Henk.

Actually, I sudo apt-get install linux-686-smp.  It showed that it was already there.  I should do sudo apt-get update linux-686-smp, or the corresponding search in Synaptic (search for 686-smp, right?). Then install.

Should I delete all the madwifi stuff first, and then update the kernel and restricted modules?  

I have visited your site and printed your dual boot .pdf.  I will see what stuff I have missed or screwed up (although Ubuntu does boot and run).  Just want to get wireless up now.  Tired of sitting in my daughter's room using an ether net cable.:-)

Best,

Roger

The latest kernel is 2.6.15-26 and should already be installed in the /boot directory if you have updated regularly. Is it a choice in the boot menu? If you're using  LILO as bootloader, then the /vmlinuz and /initrd symlinks should point to the correct versions in the /boot directory -- you can do this yourself with commands like
"sudo ln -s /boot/vmlinuz-2.6.15-26-686 /vmlinuz" and similarly for the /initrd symlink. No need to reinstall LILO if you're using the symlinks in /etc/lilo.conf; if not then change this file one last time to use the symlinks, then reinstall.

No need to take out the madwifi stuff, it won't load by itself as long as  the drivers are not listed in /etc/modules (and they shouldn't). Make sure that you have restricted-modules for the actual kernel version (there is a dependency package that ensures this). The old 386-kernel stuff can be removed (5 packages total).

Wireless, I know what you mean... I finally opted for Parallels where the VM connects to the Airport wireless through an Ethernet NIC built in software (I'm using it now).

Good luck!

---

### Post by rscow on 2006-09-05
I think I've got it.  Will check to see that it is loaded on the right directory, and then make sure the links are good.

Thanks for your help.

Roger

---

