---
title: "How to set permission to write/delete files in a usb external hard drive?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by lintroduccion on 2006-10-17
I just got a 40 gb usb external hard drive to backup some files in my laptop. Booted in Xubuntu, plugged the hard drive, made some partitions, mounted it, dragged some files to test and... it says that I don't have permissions to do such tasks.

I wonder, how can I set permissions to write/modify/delete contents on an usb external **hard** drives, that was never required when working with usb **flash** drives?

I know that it's possible with sudo command, but I don't want to start every session of thunar or any file manager with sudo before it...

maybe something with chmod? ](*,)

---

### Post by grim918 on 2006-10-17
I haven't come across this problem but you could try to chown(change owner) the drive into another user. your user name would be a good choice. Don't know if chown will work with drives though. I'll try to find out.

Maybe this thread can help you out:
[http://ubuntuforums.org/showthread.php?t=97243](http://ubuntuforums.org/showthread.php?t=97243)

---

### Post by lintroduccion on 2006-10-17
Thanks, it worked perfectly:).

---

