---
title: "Cant access windows 8 or even the hard disk"
date: 2013-10-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ayushgoyal09 on 2013-10-04
I have an ASUS A55A Notebook preinstalled with Windows 8. I tried to dual boot it with ubuntu with a ubuntu live usb disk. I'm not able to boot into windows now. Also I cant see my hard disk using the ubuntu live usb. For now I can just run my notebook using the ubuntu live disk. "I have really important data on my disk in the windows partitions (not backed up :mad: ). Can someone please help me access my data."

---

### Post by TheFu on 2013-10-04
If you just want to access data files, Ubuntu Live boots should be able to do that using the file manager.
If you want to get back to booting Win8 AND booting Ubuntu, then try **boot-repair**. My signature has links.

Please, backup your important stuff.

---

### Post by oldfred on 2013-10-04
If you left the always on hibernation or fast boot on then you cannot get to the Windows from Linux.

If UEFI boot, you should be able to go into UEFI and boot Windows. Some have to have secure boot on, most boot Windows with it off (all should per UEFI).

More info:
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by ayushgoyal09 on 2013-10-08
[http://paste.ubuntu.com/6207877/](http://paste.ubuntu.com/6207877/)
I got this on running boot repair.

---

### Post by oldfred on 2013-10-08
You did backup your system before installing?

It looks like you told the installer to erase your entire hard drive and installed the entire hard drive with Ubuntu encrypted LVM partitions.
With encryption and LVM you have added complications, but Windows and any partition with Windows recovery has been erased.
If no backup, you may be able to contact Vendor and for nominal cost get a Windows image for your system. That would not be a full installer, but a image as purchased. Or just purchase a new Windows full install.

I do not know encryption, nor LVM which full drive encryption (LUKS) requires. Ubuntu drive encryption is not for Windows. I think truecrypt is compatible with both Windows & Ubuntu if that is what you really want.

---

### Post by TheFu on 2013-10-08
> **oldfred said:**
> You did backup your system before installing?

It looks like you told the installer to erase your entire hard drive and installed the entire hard drive with Ubuntu encrypted LVM partitions.
With encryption and LVM you have added complications, but Windows and any partition with Windows recovery has been erased.

Agreed.  Looks like he **had** windows installed at 1 point and overwrote it with Linux.  I can't tell if encryption was used or not, but LVM definitely was.  I don't really do desktop installs, but with Ubuntu Server - using LVM is the default.

I really hope he had a backup 'cause the data that was there before - she is gone.

---

