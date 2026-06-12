---
title: "[HowTo] Repair the bootsector of a Windows partition"
date: 2012-02-16
forum: Any Other OS
---

### Post by YannBuntu on 2012-02-16
[B][COLOR="DarkRed"]The information in this thread is now contained in the Ubuntu community documentation located here:
[https://help.ubuntu.com/community/BootSectorFix]("https://help.ubuntu.com/community/BootSectorFix")


If you need help please create your new own thread [here]("http://ubuntuforums.org/showthread.php?t=2023420").
[/COLOR][/B]

---

If you have damaged the boot sector of one of your partitions (e.g. by installing GRUB in it by mistake), you may have troubles, eg if it's a Windows partition you may not be able to boot into Windows any more.
Here is how to repair it:

1) Run Ubuntu (works also in live-CD)
2) Install and run Testdisk, by activating the Universe repository (in your Software Sources) and typing in a terminal (Ctrl+Alt+T) the following command:
```
sudo apt-get install -y testdisk && sudo testdisk
```
3) Via the arrows and the Enter key, go to the [No log] menu,
4) then select the disk where the broken partition is,
5) then select [Proceed], 
6) then choose the type of partition (generally [Intel]), 
7) then[Advanced], 
8.) then select the Windows partition with [Boot], it will display something like :
```
Boot sector
Status: Bad

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

[  List  ]  [Backup BS]  [Rebuild BS]  [  Dump  ]
```

9) Check that you have "Status ok" below "Backup boot sector" 
10) select [Backup BS].

Done. Now you just have to reinstall GRUB into the MBR of the disk, e.g. by running [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and clicking the "Recommended repair" button.

---

### Post by YannBuntu on 2012-03-23
for information, here is an extract of a Boot-Info Summary that shows an exemple where GRUB has been installed by mistake in the bootsector of the XP partition:

```

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 108395296 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com
```

---

### Post by YannBuntu on 2012-07-20
I moved this HOWTO to the Wiki: [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by drs305 on 2012-07-20
The information in this thread is now held on the community wiki at [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [Discussion - https://help.ubuntu.com/community/BootSectorFix]("http://ubuntuforums.org/showthread.php?t=2030238")
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

Thread closed.

---

