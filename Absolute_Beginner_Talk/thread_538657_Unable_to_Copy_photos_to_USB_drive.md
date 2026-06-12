---
title: "Unable to Copy photos to USB drive"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by semjaja on 2007-08-30
i changed to ubuntu (feisty fawn) about a week ago, i am a complete noob, and even when i was using windows i wasn't that savy, but i see it as a challenge and this forum has helped me out with one or two probems that i've had, so thank your for that.
the problem i'm having now is that i can't copy photos i've edited in GIMP onto my flash drive.
i can copy and paste, but when i try and unmount the drive it says 'cannot eject volume', and when i look again, the photos i've copied are no longer there.
any advice? please bear in mind i'm a functional idiot at this at the moment.

---

### Post by kazuya on 2007-08-30
Was the drive formated in NTFS file system. If you look at the USB drive, does it say FAT32 or NTFS. To make life easy for you, you could format the drive as FAT32 . 

Then you would not have that issue. Else you may go through the slightly tricky step of using NTFS3G-fuse. This helps you write or copy files to a drive with NTFS file type format. I may have spelt this wrong.

EDIT: Any ideas guys? This is a strange one. How are you copying the files to the USB device? Are you clicking on USB drive Icon to open and then dragging the files from where you saved them to that drive. Also have you used or successfully placed files in the drive before.?

---

### Post by semjaja on 2007-08-30
if i look at it, it says File System : vfat (FAT32)
should i reformat it? if so, can you tell how to do that?

---

### Post by irish_flu on 2007-08-30
That is indeed strange.  I can say that no, I wouldn't reformat it; I'd leave it with FAT32 so that you can easily share with Windows users.

---

### Post by julian67 on 2007-08-30
> **semjaja said:**
> i changed to ubuntu about a week ago, i am a complete noob, and even when i was using windows i wasn't that savy, but i see it as a challenge and this forum has helped me out with one or two probems that i've had, so thank your for that.
the problem i'm having now is that i can't copy photos i've edited in GIMP onto my flash drive.
i can copy and paste, but when i try and unmount the drive it says 'cannot eject volume', and when i look again, the photos i've copied are no longer there.
any advice? please bear in mind i'm a functional idiot at this at the moment.

It seems your USB drive is seen as read only, that is it can't be written to by Ubuntu right now. Here are some possibilities

1st maybe the drive has a small switch on the side where you can change it between read only and read/write. 

2nd maybe the drive is formatted with ntfs instead of fat? If so then you need to enable ntfs write permissions. A simple way to do this is to install disk-manager and ntfs-3g and check the box in disk-manager that enables write support. Or format the drive as fat.

---

### Post by notwen on 2007-08-30
Launch Nautilus as root and change the permission on the whole drive, and tick the box to make sure changes go through each folder/file recursively.  Use the command below to do so.  

> gksudo nautilus

---

### Post by semjaja on 2007-08-30
thanks guys, i'll check out your advice and hopefully it works.

---

### Post by vanadium on 2007-08-30
When you unmounted, has the icon disappeard from the desktop? When you say that the photos are no longer there, does this imply that you remounted the drive, then looked in the directory to see that it is empty? I am currently also experiencing an issue where the error message "Cannot unmount" appears. However, the icon disappears anyway, the mount command shows that the drive was unmounted anyway  and it seems safe to remove the drive, thus this bug would seem to be a harmless annoyance. If you really do not see your files after mounting the drive back (remove it, then plug it back in), then you are indeed experiencing a more severe issue. It might help to post the specs of your USB drive.

---

### Post by semjaja on 2007-08-30
> **vanadium said:**
> When you unmounted, has the icon disappeard from the desktop? When you say that the photos are no longer there, does this imply that you remounted the drive, then looked in the directory to see that it is empty? I am currently also experiencing an issue where the error message "Cannot unmount" appears. However, the icon disappears anyway, the mount command shows that the drive was unmounted anyway  and it seems safe to remove the drive, thus this bug would seem to be a harmless annoyance. If you really do not see your files after mounting the drive back (remove it, then plug it back in), then you are indeed experiencing a more severe issue. It might help to post the specs of your USB drive.

when i unmount, the icon on the desktop disappears, so as you say, it looks like it's only annoying, so i remove it. when i plug it back in, the files i tried to copy are gone, but the files that were on there before (from when i was still using windows) are still there. i'll have to check the specs of the USB.

---

