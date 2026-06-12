---
title: "Dual Boot"
date: 2019-12-06
forum: Any Other OS
---

### Post by christon74 on 2019-12-06
Good afternoon fellow Ubunters_O:)  I am on dual boot: Windows7/ Ubuntu 18.04 LTS. Windows 7 is dying, and from January 2020, it will no longer be supported or be fed security updates, thus making it more vulnerable to attacks from hackers:sad:. Is it possible to replace it with another OS, or write LinuxMint over it, for example?

Thanks. Have a nice Friday, and with just a few days in advance, Merry Xmas to all of you.

---

### Post by howefield on 2019-12-06
Thread moved to the "*Any Other OS*" forum.

---

### Post by oldfred on 2019-12-06
You can have multiple installs on your system. The last install will be the default boot.
And you need to have all installs in same boot mode, all UEFI or all old BIOS. Only if on different drive can you have different boot modes, and then you have to boot from UEFI boot menu, not grub.

If multiple Linux installs, best not to use any NTFS data partitions as that needs maintenance (defrag, chkdsk, etc) from Windows or at least a Windows repair disk.

I have multiple Ubuntu installs and have installed Debian & Fedora, more just to see how they install or how grub works. My main working install is 18.04.
I like to have smaller / (root) partition and large data partition that I can mount in other installs & have same data available. But do not share /home as if experimenting I do not want settings in one install to impact main working install.

---

### Post by christon74 on 2019-12-06
Thanks Oldfred for quick answer. I never boot from UEFI, I have never tried. I usually boot from Grub. I have tried upgrading from Windows 7 to Windows 10 unsuccessfully: The Windows7 product key is not recognized. Hardware is Fujitsu-Siemens Esprimo E5731 E-stars and I have a Western Digital Hard Disk which I only use to save documents, videos and sound files_ There is absolutely no OS present on this external hard disk. Now I am just wondering what would happen if I use Gparted to completely erase the windows7 partition? How would this affect Grub and would it still let me boot Ubuntu 18.04? Would I then be able to add another Linux OS or would this **** up everything?

---

### Post by oldfred on 2019-12-06
Depends on configuration.
May not hurt to just document what you now have. On line version only says for a relatively short time. If you want to keep a copy, you need to save that yourself.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by crip720 on 2019-12-06
IF you google around you would find legal ways of installing Win 10 for free still, if you wanted Win 10.  It is usually quite safe to install other Linuxes over Windows, just make sure of your partitions and don't install on wrong one.  Grub works with both old bios and newer UEFI.  Win 7 was usually installed with bios, but make sure which one you are using.

---

