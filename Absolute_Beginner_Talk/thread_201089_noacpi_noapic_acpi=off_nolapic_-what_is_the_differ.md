---
title: "noacpi noapic acpi=off nolapic -what is the difference?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by xoros on 2006-06-21
I have seen these terms mentioned... can someone point me to what they do exactly and tell me the differences between them?  I know they go into the kernel line as boot up options... but what exactly are they doing?

noacpi noapic acpi=off nolapic

Thanks.

---

### Post by munckfish on 2006-06-21
I found this a while back which has all sorts of useful info on these sorts of boot prompt options. 

[http://tldp.org/HOWTO/BootPrompt-HOWTO.html](http://tldp.org/HOWTO/BootPrompt-HOWTO.html)

Also digging around in the kernel source's 'Documentation' directory you'll find stuff. I found details on the 'vga' option in there when I was trying to understand what that was about.

[http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=tree](http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-2.6.git;a=tree)

Update: here's a page from the redhat manuals with some good boot prompt option definitions:

[http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/x8664-multi-install-guide/ap-bootopts.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/x8664-multi-install-guide/ap-bootopts.html)

---

### Post by xoros on 2006-06-21
thanks !

---

