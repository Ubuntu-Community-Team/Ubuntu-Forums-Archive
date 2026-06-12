---
title: "Reinstalling help"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-11
ok i have vista on one partition and ubuntu on anther and i wanted to reinstall both OS so i just inserted my vista installation DVD and did it thing but now when i try reinstalling it give me this GRUB Loading..... Error 22 somthing along those line.

what do i do to fix it do i have to uninstall ubuntu seperatly or somthing?

---

### Post by JoshuaRL on 2008-02-11
You mean it gave the Grub Error 22 from the LiveCD installer?  Or after reinstalling Vista did you try to get into Ubuntu again?  

Because Windows always assumes it's the only OS loaded on the drive and rewrites MBR (Master Boot Record).  Unfortunately that's where Grub lives, so if you reinstalled Vista it overwrote Grub.  If you want to keep your current configuration of Ubuntu, then I would burn off a copy of SuperGrub and use that to fix Grub.

On the other hand, if you want to install a new instance of Ubuntu, just choose the manual install method and install it to the partition that's already there.  That should work.

---

### Post by articwolf939 on 2008-02-11
> **JoshuaRL said:**
> You mean it gave the Grub Error 22 from the LiveCD installer?  Or after reinstalling Vista did you try to get into Ubuntu again?  

Because Windows always assumes it's the only OS loaded on the drive and rewrites MBR (Master Boot Record).  Unfortunately that's where Grub lives, so if you reinstalled Vista it overwrote Grub.  If you want to keep your current configuration of Ubuntu, then I would burn off a copy of SuperGrub and use that to fix Grub.

On the other hand, if you want to install a new instance of Ubuntu, just choose the manual install method and install it to the partition that's already there.  That should work.

well i put in the Vista DVD and reformatted the HD that they both lived on and after vista got done i had to enter a Driver CD and when it restated the CPU to continue installing the drives it gave me that Error 22 so i restarted a few time then i put in my ubuntu CD and i was able to boot ubuntu from the cd but it not installed

 and i cant even get to the boot menu to chose between vista or ubuntu i cant just run ubuntu and i would like to reinsatall ubtun also

---

### Post by articwolf939 on 2008-02-11
anymore ideas?

---

### Post by JoshuaRL on 2008-02-11
Okay, I think I understand.  The issues you're having I think come from trying to use the partitions already in place.  Just delete them with gparted in the LiveCD.  Then what you want is to install Vista over the whole drive, and let it do it's thing.  Then, use the Guided Partition in the install menu to partition the drive how you want.  That is by far the easiest way to do that.

---

