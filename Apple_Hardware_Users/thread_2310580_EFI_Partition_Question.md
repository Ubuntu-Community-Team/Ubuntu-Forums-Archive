---
title: "EFI Partition Question"
date: 2016-01-20
forum: Apple Hardware Users
---

### Post by dswaugh on 2016-01-20
My main bootloader for multiple OSes is on the EFI partition of SSD1, and I'm able to boot Ubuntu from this partition, even though my Ubuntu OS is on SSD2. My question is do I still need to keep grub on the EFI partition of SSD2 (where the Ubuntu OS resides), or can I delete it and just let the grub that's installed on the EFI of SSD1 boot Ubuntu? Am asking because when I start my computer, my bootloader screen shows two separate Ubuntu icons (each representing the GRUB of its respective EFI partition), but the bootloader will boot Ubuntu only from the grub that's mounted on SSD1's EFI partition. When I click the icon to directly use the grub installed on SSD2, nothing happens. Blinking cursor. Dead screen. Hence my question. Didn't know if the grub on SSD1 is automatically chain-loading to the grub on SSD2, or if the grub on SSD1 is just booting Ubuntu outright. If the latter is true, then I'd prefer to delete grub from the second SSD, so that it doesn't even appear as an option on my main bootloader screen. Thoughts anyone?

---

### Post by oldfred on 2016-01-20
Grub defaults to installing to the ESP - efi system partition on sda.
But with multiple drives, I like to have a copy of /EFI/ubuntu on the actual drive Ubuntu is installed.
Then if sda drive breaks, you should be able to directly boot from sdb drive.

Usually you have two identical ubuntu entries in UEFI, but actual boot file is shim for one and grub for the other. Shimx64.efi is the secure boot version of grub.

Post this:
sudo efibootmgr -v

---

