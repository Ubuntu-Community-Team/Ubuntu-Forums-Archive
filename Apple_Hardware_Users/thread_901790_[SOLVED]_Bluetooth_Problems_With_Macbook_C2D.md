---
title: "[SOLVED] Bluetooth Problems With Macbook C2D"
date: 2008-08-26
forum: Apple Hardware Users
---

### Post by guywithcable on 2008-08-26
When I start up my computer my bluetooth is working fine and the icon is in the tray, but after a while the icon is gone when I go to do something. Is there a way to reinitialize the adapter? I tried restarting the bluetooth service with "sudo /etc/init.d/bluetooth restart" to no avail. I also tried "sudo modprobe bluetooth" which didn't work.

---

### Post by flaggh on 2008-08-27
The solution in this thread may work for you.
[http://ubuntuforums.org/showthread.php?t=544321]("http://ubuntuforums.org/showthread.php?t=544321")

---

### Post by guywithcable on 2008-09-03
That worked. Thanks.

To others with this problem, don't forget to set the script to be executable. :)

---

### Post by cyberdork33 on 2008-09-03
> **guywithcable said:**
> That worked. Thanks.

To others with this problem, don't forget to set the script to be executable. :)
excellent. Please mark this thread as solved (Thread tools menu).

---

