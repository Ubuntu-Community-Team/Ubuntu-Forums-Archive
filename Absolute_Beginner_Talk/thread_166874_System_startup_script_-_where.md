---
title: "System startup script - where?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2006-04-27
I am pretty sure that the boot process follows a script.  Where can I find the script that controls booting such as setting up networking and syncing to ntp.ubuntulinux.org (or is it com?), starting GDM, that kind of thing?

I want to add a small shell script to the boot process just before it loads GDM.

---

### Post by frodon on 2006-04-27
Put your script under /etc/init.d and make it executable then run this command : ```
sudo update-rc.d *script_name* defaults
```It will add your script in the boot process with a default level (it will be launched before GDM).

---

### Post by zerhacke on 2006-04-27
Thank you very much!  I'm learning shell scripting.  The script I want to add just asks the user's name, does a read, the echos welcome (read name).  Simple, but I'm just beginning so it's all I got right now.

---

