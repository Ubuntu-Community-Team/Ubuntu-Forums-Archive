---
title: "Virtualbox booting Ubuntu 12.10 from a USB stick"
date: 2013-01-30
forum: Any Other OS
---

### Post by 2Belsewhere on 2013-01-30
Guided by Pendrivelinux I finally succeeded in being able to boot my Ubuntu 12.10 under Virtualbox running under XP Pro.

The guidance given on [http://www.pendrivelinux.com/boot-a-usb-flash-drive-in-virtualbox/](http://www.pendrivelinux.com/boot-a-usb-flash-drive-in-virtualbox/) describing use of the VBoxManage internalcommands createrawvmdk -filename needed amending in my case.
The 'userprofiles' on my XP installation are 'linked' to their respective profile directories on a second hard drive using SysInternals junction.exe command.

Running Pendrivelinux's step 5 using the %USERPROFILE% system variable produced a new ..\.virtualbox directory on the XP system drive, ignoring the same in the userprofile linked directory.

I needed to remove and re-install Virtualbox and run that step 5 above fully expanding the 'real' target userprofile directory. All had then worked superbly!

(n.b. all latest versions were used)

---

