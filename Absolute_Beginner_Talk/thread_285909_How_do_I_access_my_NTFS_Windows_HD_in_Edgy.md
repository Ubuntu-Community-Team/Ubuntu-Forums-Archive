---
title: "How do I access my NTFS Windows HD in Edgy?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by AirRaven on 2006-10-27
I've just jumped back into the Ubuntu fold after a 3 month break after breaking Dapper, and I'm having difficulty accessing my Windows HD from in Ubuntu.

How's it done in Edgy? In Dapper and Breezy I just went to Administration->Disks. The function's gone in Edgy- how's it done these days?

I'm looking for a GUI tool- I'd rather not go through the terminal method if possible.

**EDIT**: Thanks folks. Once again the Ubuntu community springs to the rescue. You're all awesome. :)

---

### Post by renzokuken on 2006-10-27
well i always found editing the fstab file much easier.

just search the forums for "fstab" and "ntfs" and you should get a proverbial bucket load of threads

---

### Post by jpkotta on 2006-10-27
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)

---

### Post by CatKiller on 2006-10-27
> **AirRaven said:**
> I'm looking for a GUI tool- I'd rather not go through the terminal method if possible.

I'm not sure that there is one. The terminal's not too scary, and if you already know the mount command that you want to use, you can use Alt-F2 to have the box go away once you've run the command.

I haven't got any unmounted hard drives to check with on the computer that's got Edgy, but do you get to see your other hard drive in the Computer window? Does right-clicking on it and selecting "mount volume" work?

---

### Post by compmodder26 on 2006-10-27
These are the instructions from the Edgy Unofficial Starter Guide:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by punx45 on 2006-10-27
aww i got beat. i type too slow.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")

gives you methods for mounting NTFS manually or on boot, and with read or read / write access.   and its written for Edgy.   Light console use, looks like you can cut and paste if you dont like typing ;)

---

