---
title: "[SOLVED] Health Check?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by calelettus on 2008-01-27
Is there any tool available that can perform a health check on my 7.10 box? I just want to clean up any junk. Kinda like a Windows Registry Cleaner?

---

### Post by y-lee on 2008-01-27
See [HOWTO: Cleaning up all those unnecessary junk files...]("http://ubuntuforums.org/showthread.php?t=140920")

Also note every so often Ubuntu runs fsck at boot, this checks your system files.  You can force it do so at next reboot with

```
sudo touch /forcefsck
```.

you might also want to see [AutoFsck]("https://wiki.ubuntu.com/AutoFsck") :)

---

### Post by calelettus on 2008-01-27
Thank you!

---

