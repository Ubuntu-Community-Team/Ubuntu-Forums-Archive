---
title: "RS/6000 Install -- Apple Support"
date: 2007-07-20
forum: Apple PPC Users
---

### Post by matt_pittsburgh on 2007-07-20
Hello Everyone,

I have two questions.  First, now that Ubuntu no longer "officially" supports the PPC architecture, what are the long term plans for keeping Ubuntu on the Macintosh PPC platform?  Ubuntu is by far, my favorite Linux distro, but I was worried when I saw that official support had been dropped.  Others like Fedora and Yellow Dog continue to support PPC.  I'd really like to install 7.04 on another Mac I just acquired, but was curious if plans are to continue to support this architecture.

Secondly, do you know if Ubuntu 7.04 for PPC will install on a IBM RS/6000 that uses the PPC processor?

Thanks for the help!

---

### Post by stmiller on 2007-07-20
Ubuntu dropped paid commercial support for PowerPC Linux. They are still making PowerPC Linux releases with updates and everything. If you want support you have to come here. 

If that IBM chip is a derivative of the POWER arch, then yes Ubuntu should install fine. There are certain options in the kernel for specific IBM machines so you might have to compile you own kernel for that box. 

Use the alternative PowerPC CD and press TAB at the yaboot prompt to see options. Might have to do the powerpc64 install option.

---

### Post by matt_pittsburgh on 2007-07-20
Thanks, ST.  I appreciate the feedback.

Good news...  You were right.  I'm glad Ubuntu will still be around.  I just finished the install on the new machine and am using it now.

Better news...  The PPC version IS installing now on the RS/6000 and has had no issues identifying the hardware.

Thanks for the reply.  I do appreciate it!

---

