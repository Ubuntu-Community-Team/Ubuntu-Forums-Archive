---
title: "Boot question ( checking all file systems)"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by sunyeqi on 2006-08-05
Hello, all!

When I boot, in 'checking all file systems' phase, it says "Buffer I/O error on device hda1, logical block 1067195",
and many messages like this, the block number is consecutive.

I think it is because there is windows xp system on hda1,and it is fat32 file system.

after read the forum, i found i should modify /etc/fstab. Is it correct? But now, i cannot access to that file. I have tried 
Ext2IF in windows, but it says make sure umount the drive before shut down the linux.

Maybe my description is not clear, but please give me some advice, I am new to linux.
Thank you !,

---

### Post by orb9220 on 2006-08-05
Can you boot into ubuntu?

If you can then open a term and
sudo gedit /etc/fstab

This list the devices that are checked.
To turn off checking on the xp drive find the line that describes the xp drive it will have a fat32 or ntfs for file type.

The end of that line is probally a 0 2 which if you change the 2 to a 0  and save.

Now linux will not check that drive at boot up.

Hope this helps.

---

### Post by sunyeqi on 2006-08-05
Thanks for your reply.

I just can not boot to Ubuntu.

---

