---
title: "Setting Permissions on Windows Shared Files"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2006-12-27
I have samba installed, but I'm not using it as a server. I'm just using it to view shared files on a windows computer. If I open the file browser, click go->network I get on the windows network and can read write execute files. However, if I mount a windows network folder under /mnt/shared (adding an etry into fstab) I only have read privledges. I tried chown and chmod, but it doesn't work. The file owner is 'root' and I can't add / delete files. Is there an easy way to change this?

-Andrew

---

### Post by freebeer on 2006-12-27
have your preceded your chown command with 'sudo' (without the quotes)?  You need to give yourself superuser privileges to change root permissions, I believe.

---

### Post by Atreus12 on 2006-12-28
> **freebeer said:**
> have your preceded your chown command with 'sudo' (without the quotes)?  You need to give yourself superuser privileges to change root permissions, I believe.

Yes

Do I need somthing special in the fstab to mount it as an owner?

---

### Post by freebeer on 2006-12-28
hmmm... I'm a noob with Linux in general, so I'm not really sure why you can't change permissions.  I noticed that my samba share is owned by root, too.  (I never noticed before, so I just learned something! :D )

I followed this howto:[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605) if it's any help.  A quick perusal of the instructions seems to indicate that there's no need to mount anything.

---

