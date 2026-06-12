---
title: "vmware server not starting after reboot"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by hayward room on 2007-05-02
I have just installed my vmware server and was starting before reboot. System asked me to reboot and now it is not starting anymore, no errors nothing - just stated starting but it's not bringing up the console. 

Can someone help, please be gentle I'm an absolute beginner on this. Thanks! :)

---

### Post by hayward room on 2007-05-02
> **hayward room said:**
> I have just installed my vmware server and was starting before reboot. System asked me to reboot and now it is not starting anymore, no errors nothing - just stated starting but it's not bringing up the console. 

Can someone help, please be gentle I'm an absolute beginner on this. Thanks! :)

Also just a quick background I got in some website: 

I tried this advice given to me but got this output. 

$ sudo /etc/init.d/vmware start
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

How do you configure vmware to start? Thnx again!

---

### Post by pete on 2007-05-02
From the message you got, I'd guess the that system requested a reboot because of a kernel update.  Same thing happened to me after the first time I installed VMWare Server.

VMWare was working after you installed it because it was configured for the kernel your system was running.    Then you get a kernel upgrade via automatic updates.  Once you rebooted, your system is now running a new kernel, and it busts VMWare.

To fix it, just run the "/usr/bin/vmware-config.pl" command in Terminal (I think it requires sudo, but can't remember off the top of my head), which will step you through the same series of prompts as when you initially installed VMWare.  Just answer them all the same as you did the first time through, and you should be all set.  Nothing in you guest OS should be affected/changed.

Note, you'll have to go through this same process whenever there's a kernel update.

---

### Post by hayward room on 2007-05-04
> **pete said:**
> From the message you got, I'd guess the that system requested a reboot because of a kernel update.  Same thing happened to me after the first time I installed VMWare Server.

VMWare was working after you installed it because it was configured for the kernel your system was running.    Then you get a kernel upgrade via automatic updates.  Once you rebooted, your system is now running a new kernel, and it busts VMWare.

To fix it, just run the "/usr/bin/vmware-config.pl" command in Terminal (I think it requires sudo, but can't remember off the top of my head), which will step you through the same series of prompts as when you initially installed VMWare.  Just answer them all the same as you did the first time through, and you should be all set.  Nothing in you guest OS should be affected/changed.

Note, you'll have to go through this same process whenever there's a kernel update.

Thanks Pete! I have tried it and it works now. :) 

Cheers!

---

