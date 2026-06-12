---
title: "Final step on triple booting issue. Installing Ubuntu."
date: 2008-03-09
forum: Apple Intel Users
---

### Post by fredscripts on 2008-03-09
Hi!

I've been trying to triple boot on my macbook for some weeks. After partition the 120GB hard drive more than 10 times and tried to install windows and ubuntu a lot of times without success I think I'm finally just about to get triple booting.

The situation is: I have a perfect dual booting. Mac OS X Version 10.5 and Windows XP SP2. When I boot the macbook REFIT appears and I can choose between both.

I have a 30GB partition on the HD of ext3 type ready for Ubuntu 7.10 (I'm attaching two images). I have Ubuntu 7.10 LiveCD ready to proceed.

The question is, if I boot with the Ubuntu 7.10 live CD and proceed as a normal installation installing Ubuntu on the 30GB ext3 partition, will grub manage all the situation and let REFIT do the work in order to triple boot with REFIT at boot time?  or will grub go crazy given the situation and I won't be able to boot windows XP or Mac OS?

So please I'm so glad I've got to this point, please I'll be so grateful if you give me some advise on how do I finally install Ubuntu 7.10 on the macbook with triple booting.

Thanks you very much in advance!!

---

### Post by johnsdr on 2008-03-09
I have same problem....

---

### Post by cyberdork33 on 2008-03-09
Please stop posting a new thread everytime. Just reply to your current thread.

Install grub to the Ubuntu partition, then you will only see grub when choosing Linux in rEFIt. See the link in my signature about multi booting for details.

---

### Post by fredscripts on 2008-03-10
Thanks for answering. Sorry about creating a new thread, I was just very exited I was about to get triple booting!

So if I proceed with the Ubuntu 7.10 LiveCD, on the partition section during the installation, I need to configure something on the ext3 partition? (I mean I have to tell that partition that has mountpoint "/"?).

I've read the link of your signature, so I imagine that there will be no problem if I do a normal installation of Ubuntu 7.10, I'll be able to triple boot at refit time.

Thanks!

---

### Post by cyberdork33 on 2008-03-10
> **fredscripts said:**
> So if I proceed with the Ubuntu 7.10 LiveCD, on the partition section during the installation, I need to configure something on the ext3 partition? (I mean I have to tell that partition that has mountpoint "/"?).Exactly, choose to partition manually, and set the ext3 as /. Make sure not to auto mount the EFI partition.

---

### Post by fredscripts on 2008-03-10
Thanks for answering!!

Sorry for newbie question, but how I make sure about not auto mounting the EFI partition?

---

### Post by cyberdork33 on 2008-03-10
> **fredscripts said:**
> Thanks for answering!!

Sorry for newbie question, but how I make sure about not auto mounting the EFI partition?
Same way you set the ext3 partition to '/'. You just set it to 'do not use'

---

### Post by fredscripts on 2008-03-10
great!!!!!!!!!!! I finally got a perfect triple booting!!!!!! at refit time 3 pictures with Mac OS, Linux and Windows are given me to choose which OS boot with!!!!:):):)


Thank you very much for all your help!!!!

---

