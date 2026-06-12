---
title: "Adding new IDE HDD"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by nvdparker on 2007-05-22
Hi,

This problem seems to be related to GRUB, but I am not sure how do I go about it. I searched but I couldn't find anything related to my specific problem.

I have two 2 SATA HDDs, one of them has WinXP installed and an IDE drive with Ubuntu installed. I have configured the BIOS to boot from the IDE so that GRUB menu loads which would let me choose which OS I want.

Recently I added a used IDE HDD as a slave to the Ubuntu HDD (same channel). Now when the GRUB menu appears I can select and load Ubuntu without any problems but when I select WinXp, I get the message "**NTLDR is missing**". If I reconfigure my BIOS to boot directly from the first SATA HDD, WinXP loads fine.

So I believe the GRUB menu list has to be edited, but I don't know how exactly for this setup.

Can anyone please help me out?
Thanks.

---

### Post by overdrank on 2007-05-22
> **nvdparker said:**
> Hi,

This problem seems to be related to GRUB, but I am not sure how do I go about it. I searched but I couldn't find anything related to my specific problem.

I have two 2 SATA HDDs, one of them has WinXP installed and an IDE drive with Ubuntu installed. I have configured the BIOS to boot from the IDE so that GRUB menu loads which would let me choose which OS I want.

Recently I added a used IDE HDD as a slave to the Ubuntu HDD (same channel). Now when the GRUB menu appears I can select and load Ubuntu without any problems but when I select WinXp, I get the message "**NTLDR is missing**". If I reconfigure my BIOS to boot directly from the first SATA HDD, WinXP loads fine.

So I believe the GRUB menu list has to be edited, but I don't know how exactly for this setup.

Can anyone please help me out?
Thanks.

HI, this worked for me once. You maybe able to reinstall the grub from the live cd with the new drive in place following this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope this helps good luck!

---

### Post by nvdparker on 2007-05-23
Overdrank, thanks for the link, but I didn't think I would have to reinstall GRUB. Isn't there anything else I can do? As I see it, GRUB does not detect the new HDD or it tries to boot from new HDD.
In other words GRUB is plain confused as to which HDD contains the WinXP boot i.e 'NTLDR'.

I still feel GRUB list needs to be slightly edited. 
No offense Overdrank, but I think I need a second opinion.

Is there anyone who can help me with GRUB??

---

### Post by confused57 on 2007-05-23
Before you try editing grub, you might want to set the hard drive boot order in bios to:
IDE Master
SATA#1
SATA#2
IDE slave

If this doesn't work, then set your hard drive boot order to the way you had it & edit /boot/grub/menu.lst...your SATA Windows drive has probably become (hd2) to grub, instead of (hd1), so all you'll probably need to do is change root to (hd2,0) & change mapping lines to (hd2)...you also "might" need to change your /boot/grub/device.map for your Window's drive to be (hd2), I'm not sure.

---

### Post by nvdparker on 2007-05-23
confused57, thats exactly how I had set the boot order.

I went through the menu.lst a couple of times but I couldn't figure out what needs to be changed. I will post the contents of menu.lst in about 3 hrs time and maybe then you could point out to me what to change.

Thanks.

---

### Post by confused57 on 2007-05-23
> **nvdparker said:**
> confused57, thats exactly how I had set the boot order.

I went through the menu.lst a couple of times but I couldn't figure out what needs to be changed. I will post the contents of menu.lst in about 3 hrs time and maybe then you could point out to me what to change.

Thanks.

You might also want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

as well as:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

---

