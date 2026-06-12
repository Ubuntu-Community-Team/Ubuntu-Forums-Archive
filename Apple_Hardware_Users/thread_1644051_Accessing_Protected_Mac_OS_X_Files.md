---
title: "Accessing Protected Mac OS X Files"
date: 2010-12-12
forum: Apple Hardware Users
---

### Post by Synan on 2010-12-12
I'm a frequent Ubantu user, and keep a boot disk on hand, which I use to access the files on crashed computers to recover data for people. I've never had any problems in the past as I've only gotten Windows computers. I've been asked to look at a Macbook Pro with OS X 10.4
I can access most of the files except for the user's Desktop, Pictures, Movies, Music, and Library. I'm told that I don't have the permissions required.
The Mac has never been password protected, and I can't run the computer with OS X to change any of the settings. I don't want to use a recovery CD until I have all of the user's very important files.
Is there a way to remove the permission requirement or at least access the files? I can cause whatever damage I want to the OS X core files since I'm reformatting once I'm done, just the documents/pictures/ect. need to be left intact.

---

### Post by yugnip on 2010-12-18
I would find another mac and boot the troubled HD in "target mode". You will have to use firewire to connect to the other mac, then press and hold T while booting the troubled drive. You will then see the troubled HD on the other mac desktop, and should be able to access it's files without permission troubles. If the troubled HD is too corrupted to boot in target mode, connect it via usb/firewire to the other mac, then run repair disk in Disc Utility. See if it can repair the disc enough to boot into target mode.

Check this article for more on [Target Mode]("http://support.apple.com/kb/ht1661")


Hope this helps.

---

### Post by Synan on 2010-12-18
Thank you. I ended up reinstalling OS X and archiving (came on the recovery disk). The computer saved all of the user's files and data, and the computer turned on as if it had never crashed.

---

### Post by skullmunky on 2010-12-28
Glad it worked.  In case you need it in the future, the easiest thing is probably to use sudo to copy the user's files:

```

sudo cp -a "/media/Macintosh HD/Users/crashy" /media/backupdisk 

```

the permission problem is because HFS+ supports unix style permissions, so when the drive is mounted they are respected by linux.  Naturally the UID and GID are different though so that makes them inaccessible unless you sudo or create a custom user with the same UID and GID as the OSX user.  

you don't see this problem on NTFS disks because the permission scheme is so different that linux just mounts them with permissions disabled.

---

