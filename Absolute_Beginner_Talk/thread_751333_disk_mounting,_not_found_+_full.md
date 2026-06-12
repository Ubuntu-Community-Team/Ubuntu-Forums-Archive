---
title: "disk mounting, not found + full"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by robintoal on 2008-04-10
friends, I have preciously received help on here when I could not mount my external hard drive, that was initially solved with the "sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force" command. However this no longer works, I only tried it twice a week or so ago, and now I get a message stating "Failed to access '/dev/sdb1': No such file or directory"

Also when I hook up my horrible chinese usb drive it recognises and mounts, and even plays, but insists that the disk is already full when I try to add anything, but it's patently not. Any suggestions? RT

---

### Post by MrFSL on 2008-04-10
When you plug in a drive give it a second to register with the computer.

1) You can check what is plugged in via USB by typing:
```
lsusb
```

2) You can check what drives are connected by typing:
```
cat /proc/partitons
```

3) You should not need to type "sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force" to mount your external...  Instead I suggest installing the package ntfs-config:
```
sudo apt-get install ntfs-config
``` After install go Applications > System Tools > NTFS Configuration Tools and check the box to enable support for externals.

Now... as far as your particular problem, the drive that once worked has probably a changed  device name: (i.e. it is no longer located, or not currently located at /dev/sdb1), #2 above will tell you that. Auto-mounting the drive will overcome this and can be accomplished using #3 above.

As far as the "horrible chinese usb drive" goes - post the output of:
```
mount
```

Hope this helps.

---

