---
title: "How can I mount and unmount usb drives???"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by FarmerReg on 2007-12-21
Can some one tell me how I can mount and unmount my external usb drives??
The only way I can get the one of the drives to mount is to reboot my pc, but when I try to unmount the drive, I get a message saying I'm not privileged to unmount the drive.

And the other problem I have is that when i try to use the NTFS tool on the other drive, i still cannot write to it.

Any help would be greatly appreciated.

---

### Post by Xiong Chiamiov on 2007-12-21
I don't know about your second problem, but as for the first, you need to use sudo, eg
> sudo umount /dev/sda1
If you want to be able to unmount it in the gui, you can change a setting in your fstab (/etc/fstab) to give mounting and unmounting permissions to standard users.  I'm not sure off the top of my head, but I think it's adding either user or users to the options part (eg. /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0) <-- that's just an example from mine, you don't need all of that

---

### Post by shadow-of-sin on 2007-12-21
As for your second problem, by "NTFS Tool" do you mean ntfs-3g?

Also, can you post the contents of your /etc/fstab file?

BTW your USB drives should auto-mount

---

