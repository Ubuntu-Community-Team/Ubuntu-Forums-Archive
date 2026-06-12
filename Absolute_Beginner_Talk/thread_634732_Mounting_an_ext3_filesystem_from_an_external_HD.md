---
title: "Mounting an ext3 filesystem from an external HD"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Matt Nichols on 2007-12-08
I recently purchased an external HD (a Seagate FreeAgent), and it was formatted as nfts. I wanted it to be ext3, so I used gparted to change it so. But then it failed to mount automatically, so I modified the /etc/fstab file by adding this line:
/dev/sda1 /media/sda1 ext3 defaults 0 0
and then making the directory /media/sda1 (the drive *is* sda1). I rebooted, and now it mounts as "sda1", but I only have read privileges (I think; I can only view the contents of the drive, which is nothing, and I get the error that I do not have permissions to write to the folder when I try to do so). This completely defeats the purpose of an external HD, and I will be really bummed if I can't get this to work. So some help would be *greatly* appreciated. Thanks.
Also, what do I need to do to make it work with Windows too? If it works with Ubuntu (assuming I find a workaround, with your help, to the aforesaid problem), will it work with Windows?

---

### Post by yabbadabbadont on 2007-12-08
With the drive mounted, open a terminal window and run:
```
sudo chown yourusername /media/sda1
```
Replace yourusername with your user name.  ;)

You should then be able to create/delete files/directories on the drive.

---

### Post by Matt Nichols on 2007-12-08
Sweet, thanks! This perfectly gives me rw permissions. But it still says I don't have the permissions to unmount the drive. Is there a workaround to this too?

---

### Post by taurus on 2007-12-08
```
**sudo** umount /media/sda1
```

---

### Post by yabbadabbadont on 2007-12-08
The entry you posted from your /etc/fstab for this drive causes it to be mounted automatically at boot.  If you want to change it so that you have to mount and unmount it yourself, then change:
```
/dev/sda1 /media/sda1 ext3 defaults 0 0
```
To:
```
/dev/sda1 /media/sda1 ext3 defaults,user,noauto 0 0
```

"man mount" in a terminal window is a good thing to read if you want to learn more about filesystems and the various options available when mounting them.  :)

---

### Post by Matt Nichols on 2007-12-08
Wonderful, thank you all for your help.

---

