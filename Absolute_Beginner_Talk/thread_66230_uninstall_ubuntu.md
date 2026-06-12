---
title: "uninstall ubuntu"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by sampbar on 2005-09-16
Hi
How do you uninstall ubuntu i did something wrong in th insall and want to uninstall and reinstall ubuntu.

Thanks 

Sampbar

---

### Post by UbuWu on 2005-09-16
Just install again and format the partition you installed it on earlier.

---

### Post by jeffdano on 2005-09-21
Does this remove the bootloader (GRUB) as well?

---

### Post by rajsarkar on 2005-09-22
yes it does

---

### Post by jeffdano on 2005-09-22
Sure hope so as I have had other distro's I've "uninstalled" only to reboot and find the bootloader error out because it couldn't find Linux anywhere. I put GRUB on my hda (windows) and my linux on hdb. Will this make a difference?

---

### Post by UbuWu on 2005-09-22
Yes, grub should be on the first harddisk in the system, so it is found during boot instead of the windows bootloader.

---

### Post by jeffdano on 2005-09-23
[QUOTE=UbuWu]Yes, grub should be on the first harddisk in the system, so it is found during boot instead of the windows bootloader.[/QUOTE]

Well, reformatted the drive in question and rebooted, Threw a GRUB error 17 and stopped cold at startup. So I ended up having to reinstall Ubuntu to get the bootloader back. How the heck does one remove the bootloader/GRUB then since this didn't work?

hda- Win2k (GRUB'd)
hba-Ubuntu

---

### Post by drogoh on 2005-09-23
You don't HAVE to use GRUB or LILO, you know.  You can do dual booting with the Windows bootloader (ugly as hell but you don't have to worry about Windows duping you out of your bootloader when you upgrade service packs).  Just Google for linux ntldr and a plethora of HOWTOs come up.

Be warned, this method could destroy your house, molest your cat, change your passing grades to failing, put out an arrest warrant in no less than 15 states, change your anatomical gender or even sell you into slavery.

I'm just saying the option is out there, I give no guarantee in using it.

---

### Post by rajsarkar on 2005-09-23
If you want to dual boot XP with another Linux distro its better to use NTLoader.
However, if you want more than one linux distro along with/without Windows use Grub. 

Google for Grub configuration. 

But as others I must warn you that there is no guarantee. I tried once but failed. 

Best way is to use Grub or NTLoader with one Linux distro and one Windows ie dual booting. Over and above that if you want to install any other distro, during installation install boot program in the partition in which you are installing the distro and create a boot diskette. Use the boot floppy to boot to that particular distro. You can repeat the process for any number of linux distro.

-Raj

---

