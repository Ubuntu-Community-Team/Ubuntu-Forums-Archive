---
title: "How do I give myself permissions to alter my NTFS removable?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by freehunt on 2007-05-10
I have a removable drive that is formatted NTFS. It says root owns it, so I cannot alter anything on it, just read from it. How can I fix this without formatting it as ext3 (since I want to use it on Windows still, too)?

---

### Post by taurus on 2007-05-10
If you want to write to ntfs filesystem, then you need to install ntfs-3g.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by freehunt on 2007-05-10
Okay, I had that installed, but I had never configured it, and it was not set to enable write access for removable drives. That topic you pointed me to helped me do that. Thank you.

---

