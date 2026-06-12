---
title: "Mbr Qustion"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by BigG123 on 2007-03-19
Can you have 2 MBR's?  Like doesn't Windows and Ubuntu both create their own MBR's?  So if you have windows in the Master hard drive and attempting to install ubuntu on the slave so  would the Grub installer part of the installation would find the windows MBR and prompt you to install GRUB to that?

---

### Post by BigG123 on 2007-03-19
Can some one tell me step by step in order to install Linux on the slave to clarify this.

---

### Post by Drakkor on 2007-03-19
You overwrite the windows mbr with grub , so you'll get the option to boot to either OS
on startup. Do you have an XP disk ?

---

### Post by BigG123 on 2007-03-19
> **Drakkor said:**
> You overwrite the windows mbr with grub , so you'll get the option to boot to either OS
on startup. Do you have and XP disk ?
Yes I have the XP install disc.  But you can only have _one MBR_ right?  So Gub Deletes the windows Master MBR on installation?

---

### Post by jbayone on 2007-03-19
Yes, it replaces it, as far as i know.

---

### Post by enharrin on 2007-03-19
Yes, you have one MBR.  I think technically you could have one MBR **per disk**, but which ever disk your BIOS boots from will be the one read.

So yes, Grub overwrites the "windows" MBR (i.e., the MBR on the boot disk in your system).

---

### Post by Thirsteh on 2007-03-19
There can only be one active bootloader at any one time. Technically, you can install a bootloader to another harddrive, but that'd just be inactive, as the drive itself is not the one loaded at boot. 

As for bootloaders in general, it's possible to use the NTLDR (Windows) bootloader, but GRUB is -definitely- the easiest, and yes, it overwrites the existing MBR bootloader at installation. Are you having problems getting Windows to show up in GRUB?

---

### Post by BigG123 on 2007-03-19
No, I want to know when I install Ubuntu on the slave drive what will happen to the Windows MBR on the master drive when you install GRUB / on the slave drive.

---

### Post by confused57 on 2007-03-19
> **BigG123 said:**
> No, I want to know when I install Ubuntu on the slave drive what will happen to the Windows MBR on the master drive when you install GRUB / on the slave drive.
If your Windows drive is set up in bios to boot before the slave drive, grub will install to the Windows mbr, overwriting Windows IPL code on hda, which would be recognized as (hd0) by grub.  Grub will recognize your Windows install & add an entry to boot both OS.

If you select your slave drive (hdb) to boot before your Windows(hda) drive in bios, before you install Ubuntu...grub will install to your slave drive mbr & add an entry to boot Windows.  This method doesn't overwrite your hda mbr, you'll be able to boot Windows from grub on the mbr of hdb.  Your Windows (hda) drive will boot independently of grub, by selecting hda to boot before hdb in bios.  For me, this would be the better method of installing Ubuntu on a slave drive.

Here's how I have my system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by BigG123 on 2007-03-19
> **confused57 said:**
> If your Windows drive is set up in bios to boot before the slave drive, grub will install to the Windows mbr, overwriting Windows IPL code on hda, which would be recognized as (hd0) by grub.  Grub will recognize your Windows install & add an entry to boot both OS.

If you select your slave drive (hdb) to boot before your Windows(hda) drive in bios, before you install Ubuntu...grub will install to your slave drive mbr & add an entry to boot Windows.  This method doesn't overwrite your hda mbr, you'll be able to boot Windows from grub on the mbr of hdb.  Your Windows (hda) drive will boot independently of grub, by selecting hda to boot before hdb in bios.  For me, this would be the better method of installing Ubuntu on a slave drive.

Here's how I have my system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)Oh so you  can have multiple MBR's but the only one that works (is active) is the one to boot up first in the BIO's.

---

### Post by confused57 on 2007-03-19
> **BigG123 said:**
> Oh so you  can have multiple MBR's but the only one that works (is active) is the one to boot up first in the BIO's.
As someone mentioned earlier, each hard drive has a mbr & whichever drive you boot first, if there is code installed(Windows IPL Code or grub stage1) there, it will be "active".  See the first link in my signature for some excellent explanations of mbr, grub, bootloaders, etc.

---

### Post by BigG123 on 2007-03-19
> **confused57 said:**
> As someone mentioned earlier, each hard drive has a mbr & whichever drive you boot first, if there is code installed(Windows IPL Code or grub stage1) there, it will be "active".  See the first link in my signature for some excellent explanations of mbr, grub, bootloaders, etc.Yea, so witch ever one is set to boot up first is the one that is active.

Thanks!

---

