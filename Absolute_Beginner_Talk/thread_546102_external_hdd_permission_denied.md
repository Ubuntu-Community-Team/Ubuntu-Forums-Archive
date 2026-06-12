---
title: "external hdd permission denied"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by diatribe on 2007-09-08
I had installed virutalbox on my machine, and when I ran it it complained of me not being a member of the virtualbox group.  I used usermod to add myself to this group, which resulted in my net being able to use sudo, access my external hdd, etc.  I added my login to the /etc/group file under admin, my login, sudo, and almost every other group there is.  Everything has been fixed, other than I can still not access my external hdd.  I can access it through root, however I can not chown or access with my normal login.  Anyone have any ideas on how to rectify this?

Edit:  this actually effects all of peripheral drives, in that I can not load/burn a cd, or access my thumb drive.

---

### Post by schorsch on 2007-09-08
Are you member of the following groups:

```
adm, lp, dialout, cdrom, floppy, audio, dip, video, plugdev, usb, lpadmin, scanner, admin, vboxusers
```

These are the groups the first user on a fresh installed OS is member of except of vboxusers ... ;-)

In the future you should use
```
usermod -aG *group username*
``` to add the user to supplementary groups, otherwise you just change the primary group of the user.

---

### Post by bodhi.zazen on 2007-09-08
If you can not use sudo, you will need to boot to recovery mode to make some changes.

Recovery mode will give you root access to the CLI. You can start X if you need to(enter "startx" in the terminal without quotes), then add yourself to those groups via the group management (System -> Administration -> Users and Groups)

Or you can use nano :

nano /etc/group

Manually add yourself to the above groups

Or use groupadd from the command line.

Then you can reboot.

---

### Post by diatribe on 2007-09-08
yea I had figured out how to get sudo access by using recovery mode, and then schorsch's post had gotten my hdd working. thanks to both of you :D

---

