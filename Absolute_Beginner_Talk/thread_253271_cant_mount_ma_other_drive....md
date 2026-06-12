---
title: "cant mount ma other drive..."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2006-09-08
noob here...anyone please help me... i mounted my drive in fstab then rebooted my box but it say's "only root can mount /dev/hdd1 to... (blah blah blah yak yak yak...) please help me... thanks!

---

### Post by bodhi.zazen on 2006-09-08
In fstab use options auto,user
Ex:
```
/dev/hdxy /mount_point      ext3      user,auto  0      1
```

The drive will mount automatically at boot.

If you do not want it to auto mount at boot use "noauto,users" and it will not automount, but you will still bea ble to mount it as a user.

You may also need ot change the permissions of your mount point
```
sudo umount mount_point
sudo chown root:users mount_point
sudo chmod 777 mount_point
mount mount_point
```

---

