---
title: "Can't boot into Windows 7 after 12.04 install"
date: 2013-05-04
forum: Any Other OS
---

### Post by 53om on 2013-05-04
Hello,

I installed Ubuntu 12.04 from an iso along side Windows 7. (I've successfully already done this with another machine. Works awesome! Woo, hoo!)

After install I couldn't boot Windows. GRUB wouldn't come up to allow me to select which OS. Ubuntu would boot up just fine though. 

I tried multiple scenarios including boot-repair, although finally I decided to not install Ubuntu on the machine after all because it doesn't have a built in wireless card and getting the Netgear adapter to work started to become more trouble than it's worth (probably due to my reasonable yet admittedly limited tech skills).

Anyway...

Not being able to access Windows at all (tried the Windows System Repair disc and it says there is nothing wrong), I decided to delete the Ubuntu partition using Gparted Live CD. 

But now when booting up it tries to find GRUB and won't boot at all, giving this message:

"Verifying DMI Pool Data.......... Update Success
error: no such partition.
grub rescue>"

So my good intentions have killed (hopefully temporarily) an otherwise perfectly good machine.

Any input would be greatly appreciated!

Thanks!

PS - I know this is technically not an Ubuntu problem (not anymore anyway). But as a loyal Ubuntu user on other machines I was hoping the community would show some mercy on a poor wannabe techie :-)

---

### Post by oldfred on 2013-05-04
You should reinstall the Windows boot loader to the MBR before uninstalling Ubuntu as the grub menu is in the Ubuntu partition.

       Moved to other OS.

How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)



But if Windows will not boot, then even with the Windows boot loader it will not boot.
You may need to run chkdsk or other Windows fixes from your Windows repairCD/Flash.

---

