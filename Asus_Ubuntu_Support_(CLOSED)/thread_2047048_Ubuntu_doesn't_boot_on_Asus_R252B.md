---
title: "Ubuntu doesn't boot on Asus R252B"
date: 2012-08-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Machinator on 2012-08-24
I have bought an Asus R252B with Express Gate Cloud and installed Ubuntu on it. However it doesn't boot. It boots Express Gate Cloud if selected to boot from the hdd, just as it did before the installation.

Could you please help me with a correct grub setup?
[COLOR=#000000][FONT=Arial]
Detailed information can be found here:
[http://paste.ubuntu.com/1163916/](http://paste.ubuntu.com/1163916/)[/FONT][/COLOR]

I have installed Ubuntu root on /dev/sda6 (it's a logical partition, is it ok?). Boot device was specified as /dev/sda. 

/dev/sda1 and /dev/sda2 are probably Express Gate Cloud and restore partitions.

There is also a strange thing: boot-repair has told me that EFI is enabled, but there is no EFI partition. However /dev/sda4 seems to be an EFI partition.
/dev/sda1                  63    20,964,824    20,964,762  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,965,376    41,938,943    20,973,568  1c Hidden W95 FAT32 (LBA)
/dev/sda3          41,940,990   625,106,943   583,165,954   5 Extended
/dev/sda5         616,718,336   625,106,943     8,388,608  82 Linux swap / Solaris
/dev/sda6          41,940,992    81,000,447    39,059,456  83 Linux
/dev/sda7          81,002,496   616,701,951   535,699,456  83 Linux
/dev/sda4         625,106,944   625,142,447        35,504  ef EFI (FAT-12/16/32)

Thanks.

---

### Post by YannBuntu on 2012-08-24
Hello

Your computer has an EFI firmware (BIOS), and it is setup to boot on your live media in EFI mode.
It is probably setup to boot your hard disk in EFI mode too, so in this case you will need to install Ubuntu in EFI mode.

For this:
1) backup your documents on external disk (or DVDs)
2) via Gparted, place the boot flag on your sda4 partition
3) run Boot-Repair
4) click "Advanced options"
5) go to the "GRUB location" tab, and tick the "Separate /boot/efi partition: sda4" option
6) click the "Apply" button
7) Indicate the new URL that will appear
8.) reboot and tell us what you observe

Remark: this may not work as you have a MsDos partition table, and sda4 is far from the start of the disk. If this fails, please also show us pictures of your BIOS screens. Was this computer preinstalled with Windows? have you changed something in the BIOS? do you want to keep the possibility to reinstall Windows one day? if yes, please also create a Windows DVD.

---

### Post by Machinator on 2012-08-25
It works! Thank you very much!

---

### Post by YannBuntu on 2012-08-27
Great! :guitar:
Just for information, please could you indicate the URL provided by Boot-Repair?  (if you forgot, click the "Create BootInfo summary" and indicate the new URL that will appear)

---

