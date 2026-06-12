---
title: "XP partition Mounting Problems"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Borg on 2007-10-13
I recall this problem being mentioned before and I have fixed it on an
earlier system but I can not remember the fix.

It says when I start NTFS tool that the XP partition can not be mounted
because it hasn't closed down properly.

The XP boot just hangs at the moving bar part.

Can anyone give me the fix again please.
thanks

Oh yer running GG

---

### Post by Borg on 2007-10-13
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

---

### Post by arthur_kalm on 2007-10-22
I'm having the same problem. Here's the full output:

```
arthur@chaba:~$ sudo mount /windows/
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /windows ntfs-3g defaults,force 0 0
```

This is rather confusing... the first time after the Gusty upgrade it worked fine.... I did comment out the Dell utility drives, could this be the reason?

**Edit:** OK, I allowed for the Dell utility drives to be mounted and now Windows mounts fine. Those drives are really annoying though, so I might consider removing them...

---

