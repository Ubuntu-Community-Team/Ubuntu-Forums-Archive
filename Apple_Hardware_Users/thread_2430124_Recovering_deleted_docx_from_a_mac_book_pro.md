---
title: "Recovering deleted docx from a mac book pro"
date: 2019-10-28
forum: Apple Hardware Users
---

### Post by rjk422 on 2019-10-28
Hello!!

My wife accidentally deleted a .docx from her mac book pro and also cleared the trash.  I have been trying to retrieve the lost files by using various recovery methods using mac software without any success.  I run them from a USB so I don't chance over writing the sector that it was on.  I read where a live linux may be an option so I crated a desktop ubuntu live usb and now I'm in the mac from the live distro.  

Now I'm not sure where to go from here.

Any help will be greatly appreciated.

Thanks,

---

### Post by dragonfly41 on 2019-10-28
I do not have a Mac but I understand that testdisk can recover Mac files.
[https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=7441](https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=7441)

In general you will need to install testdisk on your LiveUSB.
But also the step often overlooked is to have another formatted USB device into which you save all recovered files.
That is, do not save files in your Mac since you might overwrite the very files you are trying to recover.

There are countless threads here on testdisk, but there are other tools to try.

[P.S.] You might need a persistent Live USB. Usually created liveUSB's are not persistent.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by wildmanne39 on 2019-10-28
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by coffeecat on 2019-10-28
> **dragonfly41 said:**
> I do not have a Mac but I understand that testdisk can recover Mac files.
[https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=7441](https://forum.cgsecurity.org/phpBB3/viewtopic.php?t=7441)

In general you will need to install testdisk on your LiveUSB.

Testdisk is for recovering lost partitions, not lost files. However, its companion program, photorec, is the one for lost files. If you install the testdisk package in Ubuntu, you get photorec as well. But it's important to run the correct application for the job intended.

@rjk422, photorec run from a live Ubuntu session would probably recover the docx file, but it's not particularly user-friendly, and you will end up with hundreds if not thousands of small recovered files, none of which will have their original filenames. Not for the faint hearted. 

That all being said, have a look at this link: [https://www.cgsecurity.org/wiki/PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec)

I see that there is a MacOSX version of testdisk/photorec. Have you investigated that?

---

