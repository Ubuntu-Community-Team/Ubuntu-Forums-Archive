---
title: "Windows 7 Boot grub rescue?"
date: 2012-12-21
forum: Any Other OS
---

### Post by MrThomsi on 2012-12-21
Hi I'm really new to ubunto and i just installed it as a dual OS, just to see if it was something for me, it wasn't, so i deleted ubunto on my windows Disk manager, now everytime i try to boot my pc it says grub rescue and i don't know what to do please, please, please i really need my pc for school

---

### Post by oldfred on 2012-12-21
Moved to OtherOS.

Since you are a Windows user you can use your Windows repairCD to fix it.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    
If you have your Ubuntu live system/install flash/CD/DVD you can install a Windows work alike boot loader.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by NcScZ on 2012-12-21
A Google search gave lots of options - these are the 1st 2

[Try here for instructions]("http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive")

[This is another option]("http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/")

---

### Post by MrThomsi on 2012-12-21
I can't access my startup menu, i think that my pc is ruined

---

### Post by rburkartjo on 2012-12-22
mrt have you tried to startup in safe mode?

---

### Post by kiyop on 2012-12-23
To MrThomsi,
> **MrThomsi said:**
> I can't access my startup menu, i think that my pc is ruined
What is "startup menu"?
Did you read [the above post]("http://ubuntuforums.org/showthread.php?p=12415705#post12415705") of oldfred?

Do not execute "sudo install-mbr /dev/sdX" (X may be "a", "b" or so). 
install-mbr (installed with package ["mbr" version 1.1.11-5, for Quantal]("http://packages.ubuntu.com/quantal/mbr")) should not be executed onto the MBR of a HDD which contains Windows VISTA, 7 and 8.
install-mbr (version 1.1.11-5, for Quantal) overwrites [disk signature]("http://www.multibooters.co.uk/mbr.html") with "00 00 00 00", which may cause failure in boot Windows VISTA, 7 and 8.

---

