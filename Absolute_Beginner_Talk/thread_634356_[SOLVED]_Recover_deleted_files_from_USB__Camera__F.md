---
title: "[SOLVED] Recover deleted files from USB / Camera / Flash / NTFS.... etc - which Apps?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-07
HI
there are several good apps under windows for recovering deleted or accidentally overwritten files, specially when it comes to camera flash memory.

I need to recover pics and **movies** from a camera flash.

(NTFS and rest can be an extra)

which apps are available for ubuntu?

they should preferably  be easy to use (with simple GUI)

thank you

---

### Post by schibs on 2007-12-07
I had a lot of success with a  program called PhotoRec to recover images off my CF card that I thought had been transferred to the computer.  :-\"

Lifehacker has a good article on PhotoRec at:

[http://lifehacker.com/software/data-recovery/download-of-the-day-photorec-161318.php](http://lifehacker.com/software/data-recovery/download-of-the-day-photorec-161318.php)

It's open source, so there is a Linux version as well as for Windoz.

---

### Post by Jimmey on 2007-12-07
Yes, photorec is teh pwnz.

```
sudo apt-get install testdisk
```

Then 

```
sudo photorec
```

from a terminal. No GUI, but as friendly as you could ask. It _will_ find some files for you, Maybe not all, maybe not intact. But a very good program.

---

### Post by aktiwers on 2007-12-07
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by tshrinivasan on 2008-02-14
This page helps.

[http://www.sleuthkit.org/informer/sleuthkit-informer-14.html#recover](http://www.sleuthkit.org/informer/sleuthkit-informer-14.html#recover)

Here is my story if recovering deleted files
[http://goinggnu.wordpress.com/2008/02/15/recover-deleted-files-from-memory-card-2/](http://goinggnu.wordpress.com/2008/02/15/recover-deleted-files-from-memory-card-2/)

---

