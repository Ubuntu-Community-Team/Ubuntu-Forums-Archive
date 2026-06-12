---
title: "Admin -&gt; Root -&gt; Admin?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by l_tenhunen on 2007-11-12
Running Kubuntu Gutsy here. I changed my accounts primary group from admin to root from System Settings. After that I rebooted as I was working with a guide. 
After booting I get the following error whenever I wish to use administration mode: *your username is unknown to sudo*.
As a result I can't run Adept Package Manager or continue tangling :oops: How can I switch my primary group back to admin or work around this?:-k

---

### Post by taurus on 2007-11-12
You need to belong to group admin if you want to use sudo.  Boot into recovery mode from GRUB menu and add your **username** back to group admin again.

```
adduser **username** admin
shutdown -r now
```

---

### Post by l_tenhunen on 2007-11-13
> **taurus said:**
> You need to belong to group admin if you want to use sudo.  Boot into recovery mode from GRUB menu and add your **username** back to group admin again.

```
adduser **username** admin
shutdown -r now
```

This worked right away. Thanks. But did it really take an emeritus professor to solve this? =D>

---

