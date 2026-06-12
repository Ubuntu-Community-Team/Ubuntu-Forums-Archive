---
title: "USB Drive claims to already be mounted"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by MonsterBox on 2005-12-11
Well, I need to transfer some files between my Laptop running Ubuntu and my PC with the DVD-burner (which is not hooked up to the internet). So, I was going to transfer the files piecemeal via my USB Attache drive.

However, after I transferred some of the files and now have come back to get some more, Ubuntu is telling me that the USB drive cannot be mounted. I see "USB Disk 2.0" in the 'Computer' area of File Browser, but when I try and access the drive it tells me:

"Unable to mount the selected volume.

Show more details

Error: device /dev/sda1 is already mounted to /media/UDISK20
Error: could not execute pmount"

I've tried searching for this issue and cannot find it. I have "man mount" and it says that to unmount a volume I need the "unmount" commant, but there's no 'man' for it and when i just try and type the command in, it tells me "command not found."

So, the question of the hour: Is there some way to force this puppy into an unmounted state, or do I have to reboot every time I unplug my USB drive and then want to plug it back in? Because if I **do**, then I'm going to have to go get myself a bigger drive.

PS - If I browse to /media/ I see a folder called UDISK20, but right-click gives me nothing that looks like it might force and unmount.

Any help? I'm totally stumped.

---

### Post by Mustard on 2005-12-11
From what I have read you would probably need to 'sync' first, to make sure that all the data is actually written to the drive and then you could use a umount command to unmount the drive.  Please not that the command is **umount** not **unmount**

So basically you would do this,

```
sync
```
```
sudo umount /media/UDISK20
```

Assuming you don't get any error messages, it should then be safe to unplug the device without any data loss.

To read the manual on sync and umount type these commands in terminal,
```
man sync
```
```
man umount
```
Press 'q' to exit the manuals and return to the terminal prompt.

---

### Post by linear on 2005-12-11
It's a shot in the dark, but...

Does the USB drive have a write-protect switch? Check that it didn't accidentally get switched to the lock position.

---

### Post by yapsuper on 2005-12-11
I might be completely off my mark, correct me if I'm wrong. You might want to unmount then manually mount the disk to another folder. For me the code was ```
su mount /dev/sda1 /mnt/usb
``` 

and as already pointed out, the command for unmount is ```
umount
```

---

