---
title: "Issue while building cros_sdk for chromiumOS on external hard disk"
date: 2015-01-14
forum: Any Other OS
---

### Post by avinashrao47 on 2015-01-14
I'm trying to sync and build chromium OS on external hard disk. I'm successfully downloaded source into external hard disk. After that, while build sdk using cros_sdk, it is throwing some error as below.
sudo: /usr/lib64/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

Not sure how to resolve the issue, I have tried few solutions from [http://askubuntu.com/questions/234603/how-do-i-deal-with-sudoers-so-must-be-only-be-writable-by-owner](http://askubuntu.com/questions/234603/how-do-i-deal-with-sudoers-so-must-be-only-be-writable-by-owner) , but failed to resolve. 

Few details as below:
$ls -l /usr/lib/sudo/sudoers.so 
-rw-r--r-- 1 root root 185288 Mar 11  2014 /usr/lib/sudo/sudoers.so
$mount -v for external hard drive 
/dev/sda1 on /media/OS type fuseblk (rw)

---

### Post by slickymaster on 2015-01-15
*Moved to ***Any Other OS*** sub-forum*

---

### Post by steeldriver on 2015-01-15
What solutions did you try, and how did they fail exactly? Please post any error messages

---

