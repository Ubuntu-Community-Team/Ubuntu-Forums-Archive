---
title: "Why the kernel I compiled can not see my SCSI disks?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2008-01-09
I compile a kernel which is linux-2.6.16.53. I set RAID and SCSI hard disks as built-in in the config. 
But when I reboot from this kernel and use

cat /proc/partitions,

I can not see my SCSI disks.

Is there any other items I should set as module or built-in? Or there is some .conf files I should edit something in?

Thanks in advance.

---

### Post by Hospadar on 2008-01-09
why do you need a home-built kernel? gutsy is on 2.6.22-14

Aside from that, you might want to go to some forums that are more technical or kernel specific forum as it'll probably be hard to find specific help here (someone might know though)

---

### Post by manmohanpv on 2008-01-09
Hi Hxsrmeng,

just curious to know, how do you compile the kernel,

could you please give me an idea about source code files as well?

-manmohan

---

### Post by Hxsrmeng on 2008-01-09
I found the reason. I need to set SATA and the driver for my sata pci card.

---

### Post by Hxsrmeng on 2008-01-09
> **Hospadar said:**
> why do you need a home-built kernel? gutsy is on 2.6.22-14

Aside from that, you might want to go to some forums that are more technical or kernel specific forum as it'll probably be hard to find specific help here (someone might know though)

Thanks.

I need work on sources. So, I need a home-built one. But I am an absolute beginner, so I come here.

---

### Post by Hxsrmeng on 2008-01-09
> **manmohanpv said:**
> Hi Hxsrmeng,

just curious to know, how do you compile the kernel,

could you please give me an idea about source code files as well?

-manmohan

I am not sure whether i caught you or not.

If you want to know how to compile a kernel from sources and where to get a sources code tarball, the book <Linux Kernel in a Nutshell> is a very good help. I downloaded it from website. 

If you want to know what I did, I borrowed the /proc/config.gz of my current working kernel, and did almost all the steps according to chapter 3,4,5,8 of above book, except that I forget to set sata pci card driver.

It's really a good book, easy to read, covers almost every important thing.

---

