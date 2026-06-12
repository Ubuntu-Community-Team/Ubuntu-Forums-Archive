---
title: "mounting usb hard drive formated with ntfs"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by ghty7 on 2007-12-08
I have read where several people have had difficulties mounting usb hard drives, but I did not find any that matched mine.   When I plug in the usb drive,  I get a msg telling me that I either have windows on my computer, or telling me to force mount.  I don't have windows and force mount didn't work.  (never figured out how to login as root!  LOL)  I decided to unplug my network cable, and the drive auto mounted fine.  I plugged the  network cable back in, and all is well.  Is there a work around this problem?  Not biggie, but I would appreciate knowing if there is a fix.  thx.

---

### Post by Hospadar on 2007-12-08
I think your problem might be that the usb drive has an unclean logfile, is though it was uncleanly removed from windows while it was mounted.  so when it gives you that command to force mount it, open a terminal (System->Accesories->Terminal) and enter in the command it gives you (if it doesn't give you one, we'll get to that later) and make sure the command begins with "sudo"

So if the command they give you is like "mount <mumbo-jumbo>", enter "sudo mount <mumbo-jumbo>"

---

### Post by ghty7 on 2007-12-08
thx  Hospadar   that was exactly my problem,  I put the drive back into windows,  unmounted with the safe removal icon, and it mounted in ubuntu fine.  I tried it with flash drives both ways and when I neglected to unmount in window properley, it would not auto mount in ubuntu.  Thanks again for the support.

---

