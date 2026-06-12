---
title: "Uninstall Ubuntu Windows 7 dualboot: grub rescue"
date: 2013-02-13
forum: Any Other OS
---

### Post by rRecupero on 2013-02-13
hey maybe someone can help me out too. I also had ubuntu 12 and windows 7 dual booted.I used Ubuntu very little but I liked it. So I decided to remove the partitions which Ubuntu was installed on.. I accepted the warning that is said that the information on the partitions would be lost if Icontinued. Everything was going fine until I rebooted. Now I get that grub rescue.

---

### Post by oldfred on 2013-02-13
Moved to your own thread in Other OS.

When you delete the Ubuntu partitions that has the rest of the grub code that grub2's boot loader in the MBR is looking for. 
You need to reinstall a Windows or Windows like boot loader to the MBR.

       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

    
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

