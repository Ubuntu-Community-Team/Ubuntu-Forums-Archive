---
title: "Windows GUI SCP with SUDO so I don't have to use root"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by bxgrant on 2007-10-08
I want to edit files remotely from a windows box.  I don't want to use VNC or FreeNX just to edit a file.  I also don't want to map drives or anything just to edit a file.

I tried WinSCP, which is great, only I don't have the permissions to edity the files since I don't want to login as root.

Does anyone know how I can edit files from a windows GUI and not login as root?

If anyone knows how to get WinSCP to throw SUDO on the front of its commands, that would work but I can't figure out how to do it.

thanks,

BX

---

### Post by cmnorton on 2007-10-08
What about adding the user who logs in using WinSCP as a sudo user. Edit /etc/sudoers using sudo visudo.

---

### Post by bxgrant on 2007-10-08
Great thanks for the reply.  I'll do that.  Is that any more or less secure than simply enabling root login?  Doesn't that mean that the user that has been added to the SUDO list has essentially all privileges of root?

thanks,

BX

---

