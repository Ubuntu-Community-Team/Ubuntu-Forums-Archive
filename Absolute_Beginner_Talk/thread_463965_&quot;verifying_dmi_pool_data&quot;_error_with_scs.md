---
title: "&quot;verifying dmi pool data&quot; error with scsi harddisk after installing"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-06-04
I built up a new computer from each parts and installed Kbuntu 7.04 amd64.
My computer has one scsi hard disk and no sata or ide type harddisk.

When I rebooted after installation, my computer has been being stucked at "Verifying DMI Pool Data'', which I have same message when I tried to boot before installation.

How can I solve this problem?

-----

After "verifying DMI pool data", I got "DISK BOOT FAILURE, INSERT SYSTEM DISK and PRESS ENTER"
When I installed, system recognize SCSI hard disk but why not on booting?

---

### Post by information_entropy on 2007-06-04
If you do not have a floppy drive make sure it is set to disabled or not installed in the bios.

If you do not have any PATA or SATA drives make sure they are all set to disabled
or not installed in the bios. 

Then enable "Reset Configuration Data"  in the bios and reboot.

Hope this works for you.

---

### Post by sundol on 2007-06-06
> **information_entropy said:**
> If you do not have a floppy drive make sure it is set to disabled or not installed in the bios.

If you do not have any PATA or SATA drives make sure they are all set to disabled
or not installed in the bios. 

Then enable "Reset Configuration Data"  in the bios and reboot.

Hope this works for you.

Thank you for your reply. :)

I did disable all IDE or floppy related option but I couldn't find the "Reset configuration Data" in my bios. This gave same result after rebooting. 

I posted a question on the company site of my mainboard. Hopefully this works for me.

---

### Post by vbdanl on 2007-07-01
hi.  i was wondering if you ever got the hd issue resolved?
i am having a similar problem.  i think i finally have decided there must be something wrong with the drive, mainly because it takes longer to go through the initial boot process than other drives on the same pc.  weird thing is ubuntu 6.06 seems to load fine on it, it just doesn't boot.

---

### Post by sundol on 2007-07-11
> **vbdanl said:**
> hi.  i was wondering if you ever got the hd issue resolved?
i am having a similar problem.  i think i finally have decided there must be something wrong with the drive, mainly because it takes longer to go through the initial boot process than other drives on the same pc.  weird thing is ubuntu 6.06 seems to load fine on it, it just doesn't boot.

I couldn't solve this problem.
Now, I am using Ubuntu 7.04 on SATA drive instead of SCSI.
If I detach SCSI, booting's done well as normal but if I attach SCSI as a data drive, then booting takes a long long time, although it boots successfully in final.

---

### Post by heot on 2007-09-01
My PC is quit simpel. But indeed no floppy drive and during upgrade of the kernel and GRUB it went wrong. My floppy drive was not disabled in the BIOS....
Ubuntu changed all lines in menu.lst from my installation disk (hd1,4) to (h0,0,)! And added the "right" UUID with it.
Happely I had another menu.lst in my Suse boot/grub with the UUID of (hd1,4) so after replacing this, all went right again.
But now I have turned off the floppy drive in teh BIOS, will it happen again next kernel upgrade?

Regards,
Henk Otten,
The Netherlands

---

