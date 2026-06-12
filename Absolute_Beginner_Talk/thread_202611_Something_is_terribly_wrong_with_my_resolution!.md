---
title: "Something is terribly wrong with my resolution!"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by petgraveyard on 2006-06-23
I was running my version of Ubuntu just fine on my 1280px width resolution, and I decided to restart and log into Windows.  On windows I use 800x600.  After I was done with Windows, I rebooted and logged into Ubuntu.  When I went in, I noticed my monitor resolution was abnormally large.  So I thought - "OK, I'll just go into screen resolution and change it".  However, when I went in there, it doesn't let me change it from 640x480!  Can anyone tell me what I can do to get it back the way it was?  Thanks in advance!

---

### Post by Jagot on 2006-06-23
Try this command in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by petgraveyard on 2006-06-23
Thanks!  After rebooting and using that command, everything is back to normal.

---

