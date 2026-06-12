---
title: "rEFlt did not update the boot options"
date: 2009-04-11
forum: Apple Hardware Users
---

### Post by baosheng on 2009-04-11
Hi, I am using rEFlt as my bootloader on my new iMac. I found that the icons or boot options did not change after the OS has been replaced. For example, I had Ubuntu on one partition. I replaced it by Windows Vista and moved Ubuntu to another partition. But the boot options/icons are still as the old one. Anyone here might be know the reason? How can I update it?

---

### Post by cyberdork33 on 2009-04-11
> **baosheng said:**
> Hi, I am using rEFlt as my bootloader on my new iMac. I found that the icons or boot options did not change after the OS has been replaced. For example, I had Ubuntu on one partition. I replaced it by Windows Vista and moved Ubuntu to another partition. But the boot options/icons are still as the old one. Anyone here might be know the reason? How can I update it?
if you are referring to the order that the icons appear, then no you cannot configure it.

---

### Post by baosheng on 2009-04-11
I am not talking about the order. The icon from which I can boot into Windows is a penguin. I think it should be a window. I also notice, if I formated the boot partition of Ubuntu, the icon is still there.

---

### Post by cyberdork33 on 2009-04-11
> **baosheng said:**
> I am not talking about the order. The icon from which I can boot into Windows is a penguin. I think it should be a window. I also notice, if I formated the boot partition of Ubuntu, the icon is still there.
I think this is because you installed GRUB to the MBR (overwriting the location of the default windows bootloader). If you had installed it to the Ubuntu partition, then you would have an icon for OS X, one for Linux, and one for Windows. It is fixable, but there is really nothing wrong with the way you are doing it now.

If you want to try to fix it, what version of windows are you using and what mac hardware and version do you have?

---

### Post by baosheng on 2009-04-11
Windows: Vista
Mac: iMac 24-inch, the latest one with 2.66 GHz CPU, 4GB DDR3 memory and NVIDIA GeForce 9400 graphic adapter
rEFLt: 0.13, the current one from rEFlt homepage

---

### Post by baosheng on 2009-04-11
Should I do fixmbr in Windows?

---

### Post by cyberdork33 on 2009-04-11
> **baosheng said:**
> 
You should identify your Mac as shown here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision")

[quote=baosheng;7056410]Should I do fixmbr in Windows?
yes, but it is a different command in vista.

First, you should reinstall GRUB to the Ubuntu partition:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Then boot your vista cd into the recovery mode, and from the console use:
```
bootrec /FixMbr
```For details on this command, see:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

