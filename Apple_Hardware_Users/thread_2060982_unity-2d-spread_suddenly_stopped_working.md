---
title: "unity-2d-spread suddenly stopped working"
date: 2012-09-21
forum: Apple Hardware Users
---

### Post by yentl on 2012-09-21
Hello! I've  installed Ubuntu 12.04 on a MacBook Pro 6,2. Initially the unity-2d-spread worked fine. However after some recent updates I found that when I click on the icon for a program of which several windows have been opened, I only get one of the windows - the one last opened. I can only see windows opened earlier after closing the later windows. Can anybody help me understand why this happened and fix the problem?

Thank you all!

---

### Post by yentl on 2012-09-29
BUMP! Sorry to bump my own thread, but this problem really has been irritating. Help would be appreciated :).

---

### Post by yentl on 2012-10-13
Recently just managed to solve the problem myself - the problems were caused by the nvidia-settings and nvidia-settings-updates packages, which probably interfered with the working of the Xorg driver despite not actually installing the nvidia driver. Once I removed these by running sudo apt-get remove unity-2d-spread was working again! I inadvertently installed these as part of Ubuntu's updates. Perhaps in future Ubuntu could not include these updates for those that do not have nvidia drivers installed on computers with nvidia graphics cards...

---

