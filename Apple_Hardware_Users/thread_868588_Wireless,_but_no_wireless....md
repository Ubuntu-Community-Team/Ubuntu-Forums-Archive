---
title: "Wireless, but no wireless..."
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by kdb424 on 2008-07-24
I have a macbook pro, and installed the wireless drivers from the bootcamp partition (windows XP), and the drivers are still installed, and I have an edit wireless networks option when I try to change from wired to wireless, but after one restart, and the drivers still installed, it won't show the wireless network option. I only see wired the wired option. Any ideas?

---

### Post by Brightbelt on 2008-07-24
You may be up to date, but the first thing I do is check for updates and install them. Sometimes, that'll fix the issue for me.

---

### Post by cyberdork33 on 2008-07-24
is ndiswrapper loading on bootup? Add ndiswrapper to /etc/modules

---

### Post by kdb424 on 2008-07-24
I think that I got it fixed now. Thanks.

---

