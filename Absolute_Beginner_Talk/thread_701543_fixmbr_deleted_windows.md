---
title: "fixmbr deleted windows?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by bklebel on 2008-02-19
I installed Ubuntu on my laptop some time ago.  I recently started running out of space so I decided to delete Ubuntu to free up space for Windows. I deleted the partitions from windows and when I went to restart I got an error 22. So after some reading I figured I messed my mbr.  I then booted into the XP recovery console and ran fixmbr.  Rebooted the machine and it wanted to reinstall windows.  I don't know if this is cause It has to restore the mbr files or what but I stopped it and haven't done anything to it since.  I don't see how the partitions could have been deleted I think they are still there but someone I have to access them. Any help would be appreciated.

---

### Post by randy78 on 2008-02-19
Boot into the recovery console
this time, type: fixboot
restart
Enter recover console again
type: fixmbr
Reboot

That should be able to fix it...

If not, you can give SuperGrubDisk a shot, as it has worked many a miracle for those who have found themselves locked out of their Windows install ;)

---

