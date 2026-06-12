---
title: "MacBook Pro + rEFIt + Ubuntu -&gt; No bootable device?"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by navrins on 2008-06-14
I've just gotten a new refurbished MacBook Pro, with Leopard.

I attempted to use these instructions:
   [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

to set up a dual boot OS X/Ubuntu system. I partitioned the drive. In Step 9, the question I was asked wasn't exactly as those instructions state, but I selected /dev/sda3 (the new ext3 partition) as my answer, which seemed consistent.  It went through what looked like a full installation, but on rebooting, once I select in rEFIt what should be the Ubuntu installation, I get a black screen saying only "No bootable device -- insert boot disk and press a key." I can't tell whether that message is coming from rEFIt, from grub, or from something else, and I haven't been able to get anywhere else from there except by turning off the computer.

I have tried rebooting in the Live CD, and at that point I can mount /dev/sda3 on /mnt and even chroot into it; parted shows me what I expect to see - so it's pretty clear that it DID install. Somehow, something just isn't finding the boot device. Can anyone suggest what I might have missed?

I tried using parted to make /dev/sda3 a boot partition; that didn't have any effect. I also installed lilo and ran liloconfig and lilo (because I know them reasonably well and grub not at all) and this did not have any effect.

I'm very experienced with Mandriva and used Red Hat many years ago, but this is my first time trying to install Ubuntu and my first time working with an Intel Mac.

It might be relevant that I started this process by using Leopard's Boot Camp Assistant to shrink the HFS partition and make a Windows partition, and installed Windows into it before I thought better of that and decided to try Ubuntu instead. I did use Ubuntu's installer to delete the NTFS partition and make ext3 and swap partitions, but if there's some less obvious thing I should have done, I might have missed it.

Please let me know if there's any additional information I should provide to help troubleshoot this. I'm at the limit of my knowledge here, and I can't find any evidence that anyone else has ever had this problem. 

Any advice (even links to other information) would be greatly appreciated!

Thanks,
Navrins

---

### Post by cyberdork33 on 2008-06-14
check the intel mac faq. There is a bug in the hardy installer. Use the partition tool in refit to fix it.

---

### Post by navrins on 2008-06-14
> **cyberdork33 said:**
> check the intel mac faq. There is a bug in the hardy installer. Use the partition tool in refit to fix it.

Oh. That was easy... yet apparently not quite enough. Now I just get a white screen with a penguin in the middle. Well, one step forward... I have some ideas on troubleshooting this, but if it rings a bell for you I wouldn't mind a hint.

---

### Post by cyberdork33 on 2008-06-14
> **navrins said:**
> Oh. That was easy... yet apparently not quite enough. Now I just get a white screen with a penguin in the middle. Well, one step forward... I have some ideas on troubleshooting this, but if it rings a bell for you I wouldn't mind a hint.
Read the rest of the same thread. :)

---

### Post by navrins on 2008-06-15
For the benefit of any future people to find this thread, he was NOT talking about

   [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

which is what I first found.

He *was* talking about the *Ubuntu* Apple Intel Users FAQ located:
   [http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

which redirected me to this discussion of the Hardy 'no bootable devices' error here:
   [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

which in turn sent me to a discussion of what to do if it freezes on the Tux logo here:
   [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

And yes, now I can boot into Ubuntu. Thanks!

Now to install more drivers... and then figure out whether Ubuntu is really what I wanted on here in the first place!

Navrins

---

### Post by justinlilly on 2008-10-07
Thanks navrins!

---

