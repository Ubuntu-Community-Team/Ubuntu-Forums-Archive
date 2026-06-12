---
title: "Found all the Files linked to VMware"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-23
Found all 116 files of VMware that equal up to 20gig roughly but cannot gain permission to delete them. anyone have any ideas before I scratch this ubuntu load up and start over? Man I really don't want to do that.

---

### Post by Blutack on 2007-03-23
Open a terminal (Applications --> Accesories --> Terminal and type in
gksudo nautilus
this will start the file manager with root permissions.  BE VERY CAREFUL - its really easy to hose your system when you can delete anything.
Find the VMware files and delete them, this time there should be no permission problems.

---

### Post by J11Gyro on 2007-03-23
Still cannot delete them. Not sure what to do besides reload sigh this is going to leave a mark

---

### Post by Blutack on 2007-03-23
Where are the files and what is the error when you try and delete them?  As root you should have permission to delete any file on the system.  This may sound daft but they aren't on an ntfs partition or something are they?

---

### Post by J11Gyro on 2007-03-23
No they aren't on NTFS or anything special but signing on as root in Nautilus does not give me the option for deleting for some reason. Could it be that none of the files are under root dir. but in the file system itself?

---

### Post by FXWGBill on 2007-03-25
I use Gnome-Commander and then gksu it... gives you a lot more control options.  You need to look at who owns the files and the permissions.  It might be that root owns them but the permission is read-only and you will have to change that... Gnome-commander makes tht a piece of cake

---

### Post by J11Gyro on 2007-03-26
Thanks I will load that up. I have already reinstalled and it is running better now than it ever has. Would love to get it running the version for my XP2400 but doing well with it the way it is. The only thing I have going now is the install of Avast for linux, installed and now cannot find it lol. The last time it put itself in apps, but it is playing hide and seek this time:lolflag:

---

