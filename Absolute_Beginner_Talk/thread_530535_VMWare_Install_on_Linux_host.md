---
title: "VMWare Install on Linux host"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by drmel on 2007-08-20
I am a complete and total Linux novice. I was succesully able to install Ubuntu Linux 7.04 on my PC. I want to install VMWare on Linux host and need to have the following items:
1) Real-time clock function must be compiled into kernel
        How do I check for this and if it is not compiled, how do I go about 
        compiling RTC into the kernel.
2) CONFIG_PARPORT_PC must be set to *m*
        I have determined that it is set to *ko*
        How do I rebuild and load CONFIG_PARPORT_PC as a kernel     
       module set to *m*?

Any help is appreciated. Any recommended beginner's guides to compiling the kernel?

Thanks

---

### Post by amsterdam on 2007-08-20
I installed vmware server on 7.04 with the tools. it seems to throw a few warnings howerver it still seems to install. mouse and video is much more responsive.

are you by chance using vmware workstation?

---

### Post by drmel on 2007-08-21
Yes, I am using VMWorkstation. VMWorkstation seems to install OK and I can set up a virtual machine, but when I try to launch my virtual machine I get the following message:
'Unable to change virtual machine power state: Failed to connect to peer process.'

---

### Post by hyper_ch on 2007-08-21
vmware server is in the repos (the commercial one I think) and it would be a simple install that way.

---

