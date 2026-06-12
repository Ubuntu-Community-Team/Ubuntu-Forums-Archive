---
title: "Bios not fully ACPI compliant"
date: 2014-08-21
forum: Any Other OS
---

### Post by Blix775 on 2014-08-21
So my friend gave me her Asus D550M laptop because after Windows 8 tried to update to 8.1 it messed everything up. She no longer wants Win 8 on that computer. I'm trying to setup a dual boot like I normally do but when I try to install Win 7 it gives me a BSOD and the message "...Bios not fully ACPI compliant..."I can boot Ubuntu perfectly but if I install it first, Windows will later totally clear GRUB and take away the dual boot aspect of the installation. I updated the bios to the latest version but it still give me the same problem. I've been trying to find a way around this in google and youtube but so far nothing has really helped me. Can anyone tell me how I can get around this problem?
Update : It turns out even if I install Ubuntu it simply won't boot for the hard drive. I'm checking out the options but it seems like tese new Bios are getting unnecessary complex.

---

### Post by varunendra on 2014-08-21
Have you disabled "Secure Boot" from Windows 8 or directly from BIOS settings? [https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

---

### Post by Blix775 on 2014-08-22
I did. I read that in a forum and did it and after disabling it, it booted from the disc but Windows gives me that message right after it tries to install. I also don't get why Ubuntu installed but it is not booting up from the hard drive. I noticed that the hard drive is missing from the boot up options and when I try to add it the bios just freezes. These EFI bios are not intuitive. I also noticed that when you turn on secure boot it asks for some keys from the hard drive. Could that be the problem?

---

### Post by varunendra on 2014-08-22
I am not familiar with UEFI setups either, but if you have already wiped out the previously installed windows, I guess there is no harm in trying to either reset the BIOS to factory defaults, or set it to "Legacy" mode (even if just for a test) and try installing again.

If the hard disk doesn't show up even in "Legacy" (or BIOS) mode, then I'd suspect the hardware.

---

### Post by oldfred on 2014-08-22
If you are trying to install Windows 7, are you installing BIOS mode or UEFI mode? And Windows 7 has no secure boot, so that must be off in UEFI.

If drive already is gpt partitioned Windows only boots in UEFI mode. Often installing Windows 7 default erases drive and converts to MBR (incorrectly) with BIOS boot. You can convert a Windows 7 DVD to a flash drive and update to make it UEFI installer.
If you let Windows 7 convert to MBR, it will leave the backup gpt partition table on the drive. Then Linux sees both MBR and backup gpt and does not know what you want. Or just fails. You then have to use fixparts to remove backup gpt partition table to fully convert to MBR and boot & install Ubuntu in BIOS mode.

Windows in UEFI mode also needs extra partitions.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
    
There were some articles where Microsoft wanted vendors not to update Windows 7 drivers for newer hardware. Or make it that you only could use Windows 8. But large customers complained and they have not done that yet, unless you are the first I have seen.

---

### Post by Blix775 on 2014-08-22
I'll try all of this tonight. Thanks.

---

### Post by Blix775 on 2014-08-24
I'm still trying those last things you posted, oldfred. But I still have problems getting this to run. It is definitely an EFI Bios.

---

### Post by oldfred on 2014-08-24
Windows 7 default will want to convert to MBR for BIOS boot, as it can only boot from a gpt drive with UEFI.
And if drive was gpt for Windows 8, Ubuntu probably installed to gpt whether UEFI or BIOS.

Post this.
sudo parted -l

---

### Post by steve892 on 2014-12-11
I had the same problem, I just purchased Asus X551MAV and was getting that same message.  What I did, updated bios, didn't solve the problem.  But in BIOS in Advanced section, there is an option for OS SELECTION, I chose WINDOWS 7 ( Instead of Windows 8 ) and now I can install.  Hope that helps.  It solved my problem.

---

