---
title: "mount usb drive when user is logged out"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by schen1977 on 2007-04-04
Hi all,
  I'm new to ubuntu. I'm trying to backup my home directory to a usb drive using rsync + cron job. When I log on, the usb drive is automatically mounted under /media/My Book/. But it is unmounted when I log out (???), and my backup script below failed because the target drive (/media/My\ Book/) disappears. 

rsync -avz ./homel /media/My\ Book/LinuxBox ---> didn't work after logging out

  Is an usb drive still mounted after logging out ? How can I modify the above command and make it work ? I think my usb drive is at /dev/sdb1

Thanks a lot !!!

---

