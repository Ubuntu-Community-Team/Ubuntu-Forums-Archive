---
title: "[resolved] hoary upgrade to 2.6.9 fails"
date: 2004-12-09
forum: Apple PPC Users
---

### Post by bakunin74 on 2004-12-09
Hi!
Have just made a usual upgrade from the hoary repository that contained a kernel upgrade to 2.6.9. Installation via Synaptic worked fine but after rebooting the Mac shortly after the message "starting Ubuntu" i got many lines of the same message and the same fpr the "old" config in yaboot (here the message from old):

"load /lib/modules/2.6.8.1-3-powerpc/modules.dep No such file or directory"
and then one line with:
"pivot root: No such file or directory
/sbin/init:429:cannot open dev/console
Kernel panic..."

The system worked fine before and al hoary upgrades did till now.

What can I do to make it boot again?

Thank's, bak

---

### Post by twstd3bc on 2005-01-17
I get similar messages when I compiled kernel 2.6.10.  I really need this kernel beause 2.6.8.1 has problems with USB/PCI addresses.  I think it's mainly because I don't know how to create an appropriate initrd.  Any pointers anyone?

---

