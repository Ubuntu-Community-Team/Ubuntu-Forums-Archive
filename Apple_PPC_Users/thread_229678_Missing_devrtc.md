---
title: "Missing /dev/rtc"
date: 2006-08-04
forum: Apple PPC Users
---

### Post by stryker33 on 2006-08-04
I have recently installed Dapper Drake on an iBook. Install went fine but when logging in, GNOME and nautilis fail. I realize that this is from needing to set the hardware clock. At the login screen the date is Jan 3, 1904!  At boot up it also mentioned not being aqble to connect to the Bonobobo(?) server.  This gave me the idea to attach it to my network and sure enough it booted up and had the correct date and time. However if I remove the network cable and reboot it reverts back to 1904.  After doing some exhaustive google research I came across the hwclock command. Below is my attempt to use it and the outcome:

xxxx@Ubuntu-Book:~$ sudo hwclock --systohc --debug
Password:
hwclock from util-linux-2.12r
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.

I looked in the /dev folder and there is no such file. Where would I get this file, or how do I create it? If you have a solution, could you please post it in newbie language. :)

---

### Post by rasec on 2006-08-04
My powerbook doesn't have a /dev/rtc either, it seems to use /dev/adb.

Another way to set the and date is to "sudo date -s 'MM/DD/YYYY HH:MM:SS'" and to sync the hardware clock with the software's do "sudo clock -w". You should be able to set the hw clock from the livecd if you can't log into your system.

---

### Post by stryker33 on 2006-08-04
You Rock! Fixed it just like that! Thanks!

---

