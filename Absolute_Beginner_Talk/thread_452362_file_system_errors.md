---
title: "file system errors"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by zolw on 2007-05-23
This morning a made an update, unsuccesfull: unable to write: read only...
then i restarted, multiple IO errors occured. I made fsck in recovery mode. in some blocks ive got I/O errors, forced rewrite - yes. then reboot

My filesystem still has errors. On startup ubuntu (in recovery mode or normal):

```

file system reports errors from previous mount: IO error

superblock last write time is in future. FIXED.

contains a filesystem with errors, chceck forced

```

when scan id at 100% done ive got message: fsck died exit 3 then reboot.

and situation is looping. ther is no way to start ubuntu without Live CD.

this is second major error on startup in two weeks. im getting tired.

---

### Post by Borzo on 2007-05-23
filesystem errors happen especially if you don' use the proper way to shutdown your compuer and that is system - > quit -> shutdown or from console poweroff. when you just turn off the computer by pressing the power button the filesystem sometimes gets corrupt.

This can also happen if you have a damaged disk.

try runing "fsck.ext3 /dev/your_linux_partition_here" from the live CD console.

good luck.

---

### Post by zolw on 2007-05-23
fsck find a lot of new bad blocks, after it finish scan, i reboot. then it find new ones. is there any other explanation besides of disc damgage? i dont want to throw it out if its ok. i have windows patrition on it and they are working fine. yesterday everything was ok. i always shut it proppetly. i dont know how disc can be damaged . my problems started after system update...

im lucky that i still have windows. dont trust linux ;)

---

### Post by Borzo on 2007-05-23
bad blocks usually mean damaged disk. get the appropriate diagnosic tool from your HD manfacturer, and run a surface test.

---

