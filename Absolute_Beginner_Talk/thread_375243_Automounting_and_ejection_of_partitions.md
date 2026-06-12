---
title: "Automounting and ejection of partitions"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-03-03
Had a problem yesterday with my external usb drive not being ejected (unmounted) from WindowsXP (run as virtual machine in Ubuntu with VM Player) before WinXP was shut down.
As a consequence, only one of the usb drive's four partitions (the only one with ext3 fs; the other three are ntfs) was automounted at boot and showed up as an icon on the desktop.
I eventually got the three ntfs partitions to be mountable by re-creating their mount points (all had disappeared) and adding these lines in /etc/fstab:
```
/dev/sda1       /media/SCSI0_VOL1    ntfs defaults,nls=utf8,umask=022 0 0
/dev/sda5	/media/SCSI0_VOL2  ntfs defaults,nls=utf8,umask=022 0 0
/dev/sda7	/media/SCSI0_VOL4  ntfs defaults,nls=utf8,umask=022 0 0

```

However, although I can now get all the ntfs partitions to mount, it doesn't happen automatically and I have to use "sudo mount -a".
A second problem relates to ejecting/unmounting these partitions. This was very easily done before just by ejecting on one of the icons for any of the four partitions. Now however, only the ext3 partitons can be unmounted by this means. 
Trying to eject any of the ntfs volums gives this error:
> umount: only root can unmount /dev/sda1 from /media/SCSI0_VOL1
eject: unmount of `/media/SCSI0_VOL1' failed
Of course, "sudo umount" works fine but has to be done individually for each of the three ntfs partitions.

Can anybody advise me on how to get things back to where they were?
Thanks
Paul

---

