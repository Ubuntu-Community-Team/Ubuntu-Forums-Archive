---
title: "Partitioning and duel-boot questions"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by SegaFan on 2008-01-15
I'm currently running Ubuntu on my PC as my only operating system but, unfortunately, I need to install Windows to run certain software. I want to shrink the Ubuntu partition, keeping what's already on there and add a Windows partition. I have read a lot about people doing this the other way round (starting with a Windows PC and adding a Linux partition), and I assume it can be done this way as well.

Could you walk me through how to do this? I will need as much detail as possible.

I also have some questions.

First, how does it work when it's set up? How do I select which partition to boot from when I start?

Secondly, I know this isn't exactly this forum's area of expertise, but I have bought a copy of Windows XP Home Edition and I didn't realise until today that there is a difference between the OEM version and the retail version, and the version that I bought, unknowingly, is the OEM version. It says on the package that this version must only be distributed with a new PC, and while my PC (which I built myself) has never had Windows on it before and it's fairly 'new' I have already been running Linux for a few weeks, what should I do? Was the site I bought it from right in selling it to me? I really want a full 'legal' copy of Windows with full support from Microsoft (after all I'm paying for it), should I send it back and get a retail copy? Can you even install this version in a partition? Have any of you used the OEM version?

Third question, completely unrelated to the second, when I finally have my Windows partition up and running, is it possible to somehow mount the Windows partition in Ubuntu, so for instance if I'm running Ubuntu, could I access the files on the Windows partition as well? I've never heard of this, it's just something I thought might be posssible but I have no idea if it is. It would be useful to be able to share files between the partitions to avoid duplication, because stupidly I saved money by installing a small-ish hard drive that I already regret that it's not bigger.

Thanks.

---

### Post by fiddledd on 2008-01-15
I can answer some of your questions.

> First, how does it work when it's set up? How do I select which partition to boot from when I start?

When you boot up you are presented with the Grub menu which gives you options on which OS to boot, also Recovery Mode and Memtest.

> Secondly, I know this isn't exactly this forum's area of expertise, but I have bought a copy of Windows XP Home Edition and I didn't realise until today that there is a difference between the OEM version and the retail version, and the version that I bought, unknowingly, is the OEM version. It says on the package that this version must only be distributed with a new PC, and while my PC (which I built myself) has never had Windows on it before and it's fairly 'new' I have already been running Linux for a few weeks, what should I do? Was the site I bought it from right in selling it to me? I really want a full 'legal' copy of Windows with full support from Microsoft (after all I'm paying for it), should I send it back and get a retail copy? Can you even install this version in a partition? Have any of you used the OEM version?

As I understand it the situation with OEM versions of Windows is as follows:

It is perfectly legal to buy an OEM Windows version providing you buy it with hardware. Just to clarify that, that is any hardware, a mouse, an IDE cable etc. The difference between Retail and OEM is the OEM version is tied to your Hardware after installing it. So changing any hardware means buying another OEM licence. There may be execeptions to this however and I'm sure MS website will provide the information.

> Third question, completely unrelated to the second, when I finally have my Windows partition up and running, is it possible to somehow mount the Windows partition in Ubuntu, so for instance if I'm running Ubuntu, could I access the files on the Windows partition as well? I've never heard of this, it's just something I thought might be posssible but I have no idea if it is. It would be useful to be able to share files between the partitions to avoid duplication, because stupidly I saved money by installing a small-ish hard drive that I already regret that it's not bigger.

Ubuntu will recognize your Windows partition(s) and either mount automatically or you can mount yourself. You can find guides to mount Windows partitions if needed by searching the forum.

There is a guide in these forums (somewhere) to installing Windows after Ubuntu so I won't go into any detail.

Hope that helps a bit.

---

### Post by c0met on 2008-01-15
This link is a step-by-step guide to installing Windows XP after having first installed Ubuntu. I used it and found it very useful.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by SegaFan on 2008-01-15
> It is perfectly legal to buy an OEM Windows version providing you buy it with hardware. Just to clarify that, that is any hardware, a mouse, an IDE cable etc. The difference between Retail and OEM is the OEM version is tied to your Hardware after installing it. So changing any hardware means buying another OEM licence. There may be execeptions to this however and I'm sure MS website will provide the information.
OK, this article says that since August 2005 you have been able to buy the OEM version legally without any hardware.
[http://www.soundonsound.com/sos/mar07/articles/pcmusician_0307.htm](http://www.soundonsound.com/sos/mar07/articles/pcmusician_0307.htm)
*"Previously, you could only officially buy it alongside a hardware item such as a hard drive or CPU heatsink, but since August 2005 any 'system builder' has been qualified to buy the OEM version, even a hobbyist, without having to buy any other hardware."*

The part I don't like is how it gets 'locked' to one PC. *"For this reason, never be tempted to buy a 'pre-owned' OEM disk from someone on eBay at a bargain price; not only does re-selling OEM products break their software license, but if it has already been activated on another PC you won't be able to activate it on yours."*

So say if I was to reformat the hard drive in the future, how does it 'know' that it's the same PC? And if I was to change the hardware, I might even change the motherboard some time in the future, at what point does it become a different PC? Even now, if I'm doing a duel boot with a Linux partition already on there, the installation will detect that I've got another partition and not believe the PC is new. Microsoft's website isn't much help at all, do you think I should e-mail them?

> This link is a step-by-step guide to installing Windows XP after having first installed Ubuntu. I used it and found it very useful.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
Thank you.

---

