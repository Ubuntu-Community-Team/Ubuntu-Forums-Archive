---
title: "How to remove an entry from rEFIt-menu?"
date: 2009-08-22
forum: Apple Hardware Users
---

### Post by produnis on 2009-08-22
Hi folks,

I use rEFIt to choose which OS to boot.
After a fail-install of Linux, I now have 3 entries in the rEFIt-boot-menu:
1) OSX
2) Linux1 #(fail version)
3) Linux2 #(working version)

Is there any chance to remove the fail-version from the rEFIt-menu?
This version does not exist at my HDD (as I installed the "working version" over it)
and I cannot boot from it....
...so I don't need it and like to get rid of it...

---

### Post by produnis on 2009-08-22
ah, this is a duplicate of that one:
[http://ubuntuforums.org/showthread.php?p=7828260#post7828260](http://ubuntuforums.org/showthread.php?p=7828260#post7828260)

---

### Post by charliehorse55 on 2009-08-22
I haven't used refit in a while, but I remember on the mac partition there was a folder called rEFIt, and inside it had configuration files. Look at the text files in there. One contains a list of possible startup options. you should be able to edit a file to fix this issue. 

Remember to backup the file, in case something goes wrong!

---

### Post by produnis on 2009-08-23
thanks for your answer, but rEFIt does not write anything into the conf.files.
It looks up on the fly which boot-devices/partitions are available...

---

### Post by Tu1J4kXk8NUhMz on 2009-08-23
I had this same issue. Try this out:

[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

rEFIt actually accesses a pre-written MBR file. I'm not entirely sure how or when it's written, but it can harbor some old installs from time to time. It is not quite as easy as charlie's option, but I know this one works as I've used it before for basically the same situation.

---

### Post by Dabberrific on 2010-06-03
My initial install of Ubuntu I set to boot from EFI partition by accident.  Now I have two Linux icons, one to boot from EFI and one to boot from partition 4 (correct partition).

I want to get rid of the boot linux from EFI option as that doesn't work.

I have tried replacing the MBR with a dummy as suggested...that didn't work.  I tried using a sudo dd command to erase the first 440 bytes of the MBR (where grub loader is) that didn't work.  I tried removing and reinstalling rEFIt, that didn't work.

Is there anyone out there that can help me?

---

### Post by George Wade on 2010-06-03
> **Dabberrific said:**
> My initial install of Ubuntu I set to boot from EFI partition by accident.  Now I have two Linux icons, one to boot from EFI and one to boot from partition 4 (correct partition).

I want to get rid of the boot linux from EFI option as that doesn't work.

I have tried replacing the MBR with a dummy as suggested...that didn't work.  I tried using a sudo dd command to erase the first 440 bytes of the MBR (where grub loader is) that didn't work.  I tried removing and reinstalling rEFIt, that didn't work.

Is there anyone out there that can help me?

When I had a problem I just trashed the rEFIt config, reinstalled rEFIt and it worked.  It isn't self correcting...

---

