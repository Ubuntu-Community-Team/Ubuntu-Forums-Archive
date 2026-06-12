---
title: "running ubuntu under vmware in windows host"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by carolus on 2007-12-09
Where can I find information about running Ubuntu as guest under VMWare?  I find messages in this forum about running Ubuntu as host,  but not about running Ubuntu as guest on a Windows machine. I haven't found a user forum for VMWare. 

My immediate question is whether Ubuntu as guest on a Windows machine has full (and safe) read/write access to the Windows NTFS file system.

---

### Post by Nano Geek on 2007-12-09
This looks like it would work for you, it's a bit old, but nothing should be very different. 

And no, Ubuntu should not have any trouble reading from a NTFS filesystem.

I hope you enjoy using Ubuntu. :)

---

### Post by aysiu on 2007-12-09
> **carolus said:**
> Where can I find information about running Ubuntu as guest under VMWare?  I find messages in this forum about running Ubuntu as host,  but not about running Ubuntu as guest on a Windows machine. I haven't found a user forum for VMWare. 

My immediate question is whether Ubuntu as guest on a Windows machine has full (and safe) read/write access to the Windows NTFS file system.
Try this:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by carolus on 2007-12-10
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)


Thanks, aysiu.  Virtualbox looks like an alternative to VMWare.  How does it handle the "virtual hard drive"  without risking corruption of the host NTFS file system?  What kind of read/write access does Ubuntu have to the host NTFS file system?

---

### Post by Nano Geek on 2007-12-10
> **carolus said:**
> Thanks, aysiu.  Virtualbox looks like an alternative to VMWare.  How does it handle the "virtual hard drive"  without risking corruption of the host NTFS file system?  What kind of read/write access does Ubuntu have to the host NTFS file system?Ubuntu has built-in support for the NTFS filesystem, there's no need to worry about corruption, and Ubuntu and read and write to NTFS just fine.
Tell us how it goes. :)

---

### Post by Threbus5 on 2007-12-10
Hi,

It should work ok.
It worked for me a couple of weeks ago.
Because Windows in Ubuntu showed less speed degradation than Ubuntu in Windows, I chose to run Windows in the VMserver.

Take care.

---

