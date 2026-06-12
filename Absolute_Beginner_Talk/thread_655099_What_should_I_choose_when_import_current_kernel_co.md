---
title: "What should I choose when import current kernel configuration??"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-31
hi, 

After refresh installing Ubuntu Gusty Gibbon, I am now trying to complie Kernel 2.6.23.. following the instruction from [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

And I am stuck at instruction 8 - Now import your current kernel configuration and get your current kernel options:

When I do it, I get the following message.. 


* Linux Kernel Configuration
*
*
* General setup
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] y
Local version - append to kernel release (LOCALVERSION) [] 
Automatically append version information to the version string (LOCALVERSION_AUTO) [N/y/?] n
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] y
System V IPC (SYSVIPC) [Y/n/?] y
POSIX Message Queues (POSIX_MQUEUE) [Y/n/?] y
BSD Process Accounting (BSD_PROCESS_ACCT) [Y/n/?] y
  BSD Process Accounting version 3 file format (BSD_PROCESS_ACCT_V3) [Y/n/?] y
Export task/process statistics through netlink (EXPERIMENTAL) (TASKSTATS) [N/y/?] n
User Namespaces (EXPERIMENTAL) (USER_NS) [N/y/?] (NEW) 


Here I don't know what to do?? 

What should I choose??   And after this, I had a lot of questions like this. 

I just don' know what to choose..

Could you help me out???

Thanks

---

### Post by kidders on 2008-01-01
Hi there,

> **taekr said:**
> I just don' know what to choose.I would suggest choosing 'N'. There are very few situations in which this particular option would be useful, and if it applied to you, you would probably know you need it.

In general though, you're the only person who will know how to configure kernel options that've been added since the version your .config came from. Without knowing *everything* about your hardware & how you want it configured, the best anyone else could offer you is a best guess. Making the wrong choices may break kernel features or cause odd behaviour, especially if there is a big gap between the kernel versions you're switching between.

I would suggest reading about any new kernel features you don't understand ... in most cases, you should be able to decide whether (and how) to build them, based on what you want your computer to be able to do. There's plenty of help in the kernel documentation and on the web.

I hope that helps.

---

