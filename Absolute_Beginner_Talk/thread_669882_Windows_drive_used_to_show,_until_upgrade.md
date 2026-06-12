---
title: "Windows drive used to show, until upgrade"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by swhitney2003 on 2008-01-16
2 sata hard drives, 1 windows, 1 ubuntu.

When I first installed Ubuntu (7.04) my windows drive was visible. Then I upgraded to 7.10 and now I cannot see the drive, nor get it to mount. I tried manually mounting to no avail. It appears it is in my fstab config... when I do mount -a I get an error about the drive...

"Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details."

fdisk -l does show the drive... any idea why it doesnt want to show now?

---

### Post by mikeyphi on 2008-01-17
The only thought that I can suggest - Windows often fails to get mounted if it was used and then not shut down properly........
Try booting into windows and the letting it go through its full shutdown process. This may allow Ubuntu to 'see' the os again!

---

