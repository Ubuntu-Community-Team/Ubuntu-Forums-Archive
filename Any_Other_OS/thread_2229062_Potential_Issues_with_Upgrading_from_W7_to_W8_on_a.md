---
title: "Potential Issues with Upgrading from W7 to W8 on a dual boot?"
date: 2014-06-11
forum: Any Other OS
---

### Post by cjtabb2 on 2014-06-11
Just curious, what with the UEFI boot of W8 and all. A free upgrade comes with the warranty on m computer, I believe, and W7 has been sluggish of late, so considering an upgrade. Regards.

---

### Post by oldfred on 2014-06-11
Moved to OtherOS since Windows.

How full is NTFS partition? Windows only runs well if you have 30% free. At 10% free it gets real slow.
Also chkdsk and defrag on a regular basis.

With an upgrade you would not change to UEFI unless your hardware is also UEFI capable and you totally erase hard drive and repartition to gpt. Only a few Windows 7 installs on hardware just before Windows 8 came out were installed in UEFI mode. But many newer systems with newer Intel chips have UEFI but Window 7 is in BIOS mode which has to have MBR partitioning.
How you boot install media is how it installs. Or boot installer in UEFI and it installs in UEFI. But UEFI installer for Windows will not work on MBR(msdos) partitioned drive.

But you do have to worry about hibernation/fast boot.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by cjtabb2 on 2014-06-12
ok thanks. 
It is hardly full, comp is less than a year old.
looks like a bios boot.
will run defrag.

---

### Post by LastDino on 2014-06-13
Just in case, don't forget to take backup :3

---

