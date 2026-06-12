---
title: "A problem when installing the SUSE linux on my Virtual Machine."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-08-02
I am trying to install a SUSE linux on my virtual machine. The host system is Ubuntu 1.04. (The mixed Windows XP system only has 3 M free capacity, I don't think it's good for a VM host.)

I created a new VM, and started to install the SUSE linux. Everything was fine untill the "vmware" quit automatically after "installation" but before "configuration".

I got into it with the rescue mode, login in as root, it showed no files in folder /root
I reboot from CD (iso), and repair the installation. Finally it turned out:

when checking Fstab entries, could not find existing deices for debugfs and usbfs. (So, I removed these lines.)
Failed in repair mimimal package selection. (missing smtp_daemon)
Failed in instal boot loader.

It still doesn't work. Is is anything else I can do? I really don't want to re-install it. It took me about 10 hrs last day,  though it  showed  remaining time "1:51:**". Every second actually took about 10 seconds to go :). In the meantime, my laptop was too slow to do anything else....  And, the most important thing is, I don't know what the wrong was?  And will I meet the same situation after another painful 10 hrs?

Thank you.

Actually I should make it more clearly, 
My laptop has mixed system, Windows XP and Utuntu 7.04. I am trying to install a virtual machine on the Utuntu part.

I am using VMware server 1.03 and openSUSE-10.2-GM-DVD-i386.iso

---

### Post by Kingsley on 2007-08-02
Have you given VirtualBox a try?

---

### Post by Hxsrmeng on 2007-08-02
> **Kingsley said:**
> Have you given VirtualBox a try?

No. I am required to use Vmware.  :)

---

