---
title: "can't find ntfs shared partitions"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-12-31
using dual boot XP and 7.10

XP won't boot, even in safe mode

Ubuntu boots fine

had to create new profiles in Firefox and Thunderbird as i was sharing the profiles on the XP partition

now i can't see  two ntfs partitions i just use for shared files (besides the XP partition).  i can see them with fdisk readout on terminal and Testdisk shows they are OK.  i can't manually mount with terminal as i get the following:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda5 ntfs-3g defaults,force 0 0



How do I get access to those partitions? (sda5&6)

Interestingly enough Testdisk says the XP partition is OK and can see the files on it.  Any strategy for easily recovering this would save time.

Thanks!

---

### Post by taurus on 2007-12-31
Looks like you didn't shutdown window cleanly; therefore, you would get that warning message. So, if you want to mount /dev/sda5, you have to use the force option.

```
sudo mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
df -h
```

---

### Post by sagesparrow on 2007-12-31
thanks
that mounted the 2 unseen partitions.

any trick to get XP to close cleanly if I can't boot into it?  (i know, this isn't a windows forum)

thanks for your help

---

### Post by taurus on 2007-12-31
Just don't use hibernation or stuff like that when you try to shutdown windows.

---

### Post by sagesparrow on 2007-12-31
i am getting a serious error message when trying to boot into windows.  i'm afraid at this point it's not a question of hibernating or whatnot.  just can't get XP booted in any mode.  But Testdisk says the disk is not corrupted and boot sector is intact.

---

