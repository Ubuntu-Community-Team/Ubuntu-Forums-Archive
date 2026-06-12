---
title: "Help : A Very Serious Problem"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by ubuntu_amatuer on 2007-12-04
I connected my external hard drive and was working with a folder inside the hard drive, and the USB cable plugged into the hard drive was accidentally pulled out, a message warning me that before disconnecting a hard drive I should unmount it, which is what I normally do.

When I connected the hard drive immediately after that linux would not  mount the hard drive, so I tried restarting the computer a few time and also connecting to different USB ports and would not mount. So as a last resort I connected the hard drive to a windows machine and then connected it back to Linux, it is mounting now but the folder   I was working with when the USB cable was pulled is not accessible. It is being shown as a blank icon and I am not able to access that folder.

Please help me recover that folder.

---

### Post by KudoKid on 2007-12-04
Far as i know, its corrupted because it was unplugged, its no fun when that happens, but you got lucky, many people cant access anything. Keep waiting for other replies though, it may be acceptable! =)

---

### Post by tgalati4 on 2007-12-05
Did you run fsck on it?

>sudo fsck /dev/sda4 (or whatever your drive is called when you plug it in)

A dirty file system won't mount or will only mount read-only.  It needs to be repaired before you can access it.

---

### Post by ubuntu_amatuer on 2007-12-05
It looks like fsck will not work if the hard drive is fat32 which is what the external hard drive partition is. 

How else could I handle this ?

---

### Post by Hospadar on 2007-12-05
well if the filesystem is corrupted, and fsck won't work, the only real option would be to format the drive.

However, it might not be mounting just because of a detected unclean de-mount.  you may be able to manually mount it and force mount to ignore such flags.  try having a look at the mount manual.

That said, if the FS is indeed fat32, I don't thing there is any logging of unclean de-mounts, so that's probably not the issue.  you may just need to reformat

---

### Post by ubuntu_amatuer on 2007-12-05
Thanks for that info, I am at work right now and will have a look at it see if I can do a manual mount.

---

### Post by irish_flu on 2007-12-05
It probably got a little messed up when it got disconnected in the middle of a write, or something. If it's Fat32, you might try scanning it in Windows (since it seems you have access to a Windows box).

Mount the drive in Windows (hopefully it will do that), then go to "My Computer", right-click on the drive icon, select "Properties", select the "Tools" tab, and select "Check Now" under "error Checking".

WARNING: fixing anything it finds could lose your data for you, if it's not already lost.  I'd do this as a last resort before I reformat the drive, if that's what you're gonna do.

If you can still mount the drive, COPY all the other stuff off of there (anything else you need), just in case the repair doesn't go well.

Note, I said COPY (not MOVE).  We don't want any changes written to the disk, if we can help it.

After you've copied your other stuff off, then you can try the repair in Windows.  EVEN if you do get your data back, I'd copy it off of there and then reformat the drive; I wouldn't trust it until it's been reformatted.

---

### Post by tgalati4 on 2007-12-07
fsck will fix fat32 partitions, but if the utility can't detect the partition type, it will give an error.  You could use the fat32 flavor of fsck:

>sudo fsck -t vfat /dev/hda7

---

### Post by ubuntu_amatuer on 2007-12-13
I connected the drive to a windows machine and did a disk error check and selected to fix any errors, once it did that I was able to access the lost folder.

Thanks for all the input.

So my question is this, since I am newbie, I guess I could ask this, Why does Linux mess up disk mounting without some sort of fail safe, whilst windows has never had any problems with external drives being disconnected when they are being worked on. I mean when an external drive is connected to windows and if it was inadvertently disconnected it would not make any folder or file unreadable, so why did Linux do what it did.

That being said I don't think I will be going back to windows for now, will stick to Linux and learn it quarks with time.

---

