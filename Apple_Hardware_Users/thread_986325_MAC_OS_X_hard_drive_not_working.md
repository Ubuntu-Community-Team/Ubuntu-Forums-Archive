---
title: "MAC OS X hard drive not working"
date: 2008-11-18
forum: Apple Hardware Users
---

### Post by linux_08 on 2008-11-18
Hello all..

My friend has a  macbook 10.4.11 and it can no longer boot, and she wants to be able to retrieve the files. I do this all the time with windows PC, but I have no clue if the same Ubuntu Live cd will boot a macbook or is it the same steps to mount the hard drive...any help is appreciated :-)

EDIT: She only the MACbook not the pro.  And no ubuntu partition

---

### Post by cyberdork33 on 2008-11-18
You should be able to boot the normal Ubuntu LiveCD and access the Mac partition. Keep in mind that OS X uses permissions much in the same way as Ubuntu, and thus Ubuntu will obey the permissions on those files (the livecd user account will not be able to manipulate the files "owned" by the OSX user). You will need to start a nautilus window with root priviledges to copy files to an external drive (or wherever you intend to backup the files).

---

### Post by linux_08 on 2008-11-18
hey cyberdork33 thanks a lot..so once i have the nautilus window with root privileges its going to ask me for a password or is it not? since im using the livecd user account...so there will be no mouting of the drive?

---

### Post by cyberdork33 on 2008-11-18
> **linux_08 said:**
> hey cyberdork33 thanks a lot..so once i have the nautilus window with root privileges its going to ask me for a password or is it not? since im using the livecd user account...so there will be no mouting of the drive?

I don't think the LiveCD prompts for a sudo password. you will probably have to open two windows, one with the Mac drive, and the other with your backup. Once on the backup you can mod the permissions so that they are accissible on the new OSX install.

You "mount" the drive manually, but you do not have to do it via commandline. Just go to the Places menu on the top panel of the Ubuntu desktop and click on the drive. It should show there automatically. Then an icon will appear on the desktop when it is mounted.

---

### Post by linux_08 on 2008-11-18
thanks a million dude, and thanks for telling me about the modding for the permissions to get it back to OS x once i reinstall it...i totally forgot about that, i can do that while using ubuntu live right?

---

### Post by cyberdork33 on 2008-11-18
> **linux_08 said:**
> thanks a million dude, and thanks for telling me about the modding for the permissions to get it back to OS x once i reinstall it...i totally forgot about that, i can do that while using ubuntu live right?
yes.

---

### Post by linux_08 on 2008-11-19
thanks a lot dude :guitar:

---

