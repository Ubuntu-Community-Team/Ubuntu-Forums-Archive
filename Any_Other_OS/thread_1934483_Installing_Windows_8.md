---
title: "Installing Windows 8"
date: 2012-03-02
forum: Any Other OS
---

### Post by windows8er on 2012-03-02
Hello to the community.
First of all let me apologize because I'm not sure if I'm posting at the proper forum.

Well here's my deal.
Till today I'm dual booting between Windows 7 and Ubuntu and now that the Windows 8 consumer preview is out there I want to install it too. But I'm not sure what will happen to GRUB.
So I was wondering if anyone can tell me what to do in order to have all three operating systems.

king regards

---

### Post by oldfred on 2012-03-02
Welcome to the forums.

Moved to other OS sub forum.

I do not know Windows 8. But it makes a difference if you have the old MBR partitioning or the new gpt partitioning that only boots with UEFI.

Most have MBR and the limit of 4 primary partitions. Windows only boots from a primary partition. If you install a second version of Windows it will move the boot files from the second install to the first. Windows considers the first install with the boot flag as the active partition.

Best to have good backups as any major system change can cause issues.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

You will have to reinstall grub2's boot loader to the MBR. So have your Ubuntu liveCD handy. Make sure it is the same version as you have installed if you have upgraded since install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

You should also make a Windows repair CD.
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Double.J on 2012-03-02
> **windows8er said:**
> Hello to the community.
First of all let me apologize because I'm not sure if I'm posting at the proper forum.

Well here's my deal.
Till today I'm dual booting between Windows 7 and Ubuntu and now that the Windows 8 consumer preview is out there I want to install it too. But I'm not sure what will happen to GRUB.
So I was wondering if anyone can tell me what to do in order to have all three operating systems.

king regards

I recommend a VM if you can, or use Easy BCD as your bootloader from windows 7 - grub has been a problem for me; installing it back over windows 8, just results in windows 8 forcing a boot repair that wipes out grub again!

-- Oh and made sure you burn an iso disk, don't accidentally upgrade your windows 7 with win 8!

---

### Post by sffvba[e0rt on 2012-03-02
> **gnu/mirow said:**
> -- Oh and made sure you burn an iso disk, don't accidentally upgrade your windows 7 with win 8!

Yup, been there, done that :p


404

---

### Post by windows8er on 2012-03-02
wow, really quick response. thank you all guys.
I'll study what you've posted and try to figure out how to not mess up my system.

thanks again

---

### Post by critin on 2012-03-04
Since Win8 is beta, I'd really suggest using VM for safety.

---

