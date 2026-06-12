---
title: "Ubuntu Memory max"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by riconet on 2008-02-12
I have a quickie question and hope someone could help.  There is a ram memory limit for Ubuntu Desktop (4GB Max) and I was told to edit the kernal.  I am new to ubuntu and I was also told that someone might already have a kernal which could be copied?  If this is possible I would like to know and how to copy it over to an existing installation of Ubuntu Desktop.

Once again, thanks to all here at the forum.

Rico:popcorn:

---

### Post by emarkd on 2008-02-12
The 4G limit has nothing to do with Ubuntu.  All 32-bit Operating Systems are limited to 4G because that's the largest address you can fit into a 32-bit register.

If you need to address more RAM, you'll have to install the 64-bit version.

---

### Post by riconet on 2008-02-12
Thanks for the quick response and thank you for explaining this.  I was mislead and will check into correcting my problem based on your response.

---

### Post by Joeb454 on 2008-02-12
Just out of curiosity, what Processor do you have? And how much RAM do you have?

---

### Post by BertP on 2008-02-12
Actually,  the way most 32 bit OS  are configured,  you most likely have a potential of about 3 GB  of usable RAM (because the OS reserves most of 1GB of addresses for internal use) .  If you have a 64bit CPU,  then you might be able to recompile the kernel to access more.... or, at least, that's what I have heard; I have never compiled a kernel myself.

Check-out this thread,   a  poster there  claims to recompiled his 32 bit kernel to take advantage of 64 bit addressing so that he could use all of the 4GB of the RAM installed on his machine

[http://ubuntuforums.org/showthread.php?t=574494](http://ubuntuforums.org/showthread.php?t=574494)

---

