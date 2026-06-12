---
title: "Problem after updating..."
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Rakeris on 2006-08-07
Ok, I let the updates download over night and installed them in the morning. After I restarted a number of programs under the Administration tab no longer work. They start to start up, but then fail or something. For example it says "Starting Users and Groups" it sits there for around 10 seconds, then dissappears. Others nothing happends when you click on them.

The ones that won't work are:
Users and Groups
Update Manager
Time and Date
Synaptic Package Manager
Shared Folders
Services
Networking (only way I got online was because it dialed out during start-up)
Login Window
Language Support
Disks

In other words..most of them. Would have been easier to name the ones that did work. -_-

And KPPP won't work either, I get this error.
```

You don't have sufficient permission to run
/usr/sbin/pppd
Please make sure that kppp is owned by root and has the SUID bit set.

```
It was working fine before the update as well. And yes the permissons are set correctly for that file/folder.

Everything else seems to work fine.

Any ideas?
Thanks!!

---

### Post by taurus on 2006-08-07
What groups do you belong to now?  Open a terminal and paste it here!

```

id

```

---

### Post by Rakeris on 2006-08-07
> 
uid=1000(adam) gid=1000(adam) groups=0(root),4(adm),6(disk),7(lp),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),37(operator),38(list),40(src),44(video),46(plugdev),50(staff),100(users),101(dhcp),106(lpadmin),110(scanner),111(gdm),112(admin),1000(adam)


Also, I cannot login as root in terminal I get this error.
> 
sudo su
sudo: must be setuid root


---

### Post by taurus on 2006-08-07
I don't think it is a good idea to include yourself in group root--0!!!  What happens when you run this command from a terminal?

```

sudo apt-get update

```

---

### Post by Rakeris on 2006-08-07
Hm, I'll remove that then. (When I'm able to of corse) I was having some permission problems a bit ago and was playing around with the group settings.

The same as when I try any sudo command.
> 
sudo apt-get update
sudo: must be setuid root


---

### Post by taurus on 2006-08-07
Boot into recovery mode (from GRUB menu), then edit your /etc/group and remove "adam" from group 0!  Reboot and see if you can sudo again...  You only need to belong to groups adm & admin to use sudo!

---

### Post by Rakeris on 2006-08-07
Same as before. Also, after the updates there are now 2 sets of Ubuntu in the GRUB...can I simple delete the newly made ones? Or at least the ones I assume are the newly made ones?

> 
sudo apt-get update
sudo: must be setuid root


---

### Post by Rakeris on 2006-08-07
Some bumpage.

Any help or ideas would be great. As I would rather not have to reinstall as I'd have to get my modem working again...it may go smoothly the second time, but I'd rather not have to find out. :P

---

### Post by Rakeris on 2006-08-08
Bump.

---

### Post by Rakeris on 2006-08-08
One more bumb for great justice! Before I reinstall >.<

---

