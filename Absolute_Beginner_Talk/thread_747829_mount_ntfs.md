---
title: "mount ntfs"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-04-06
i need to dual boot ubuntu and vista on my laptop only because my job prefers me not using linux for whatever reason.  well i have two hard drives and my second drive i decided to format as ntfs as a common share drive but it seems that it wont pick up on ubuntu.  it shows it there with the volume label but when i double click it gives me the following error:

Cannot mount volume.
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy
hal-storage-fixed-mount refused uid 1000



What should I do?

---

### Post by tommcd on 2008-04-07
See these from Ubuntu's documentation:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28mount%29%7C%28ntfs%29](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28mount%29%7C%28ntfs%29)
Hope this helps.

---

### Post by Living2007 on 2008-04-07
> **Aysah said:**
> i need to dual boot ubuntu and vista on my laptop only because my job prefers me not using linux for whatever reason.  well i have two hard drives and my second drive i decided to format as ntfs as a common share drive but it seems that it wont pick up on ubuntu.  it shows it there with the volume label but when i double click it gives me the following error:

Cannot mount volume.
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy
hal-storage-fixed-mount refused uid 1000



What should I do?

Go to Computer -> right click on the Ntfs drive (should appear as a removable drive) -> Click Mount Drive and type your password in.

---

### Post by superprash2003 on 2008-04-07
go to the terminal and type cat /etc/fstab  you should find your ntfs drive in there in the form /dev/hda or something.. find that .. and then type the command sudo mount /dev/hda

---

### Post by prodigy6630 on 2008-04-07
sudo mount -t ntfs-3g /dev/hda5 /media/hda5/ -o force

---

