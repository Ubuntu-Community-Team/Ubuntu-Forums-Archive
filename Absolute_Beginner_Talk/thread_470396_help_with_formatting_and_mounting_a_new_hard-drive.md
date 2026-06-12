---
title: "help with formatting and mounting a new hard-drive. fdisk unable to read device?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-06-10
i just bought a new 300gig hd, and want to install it as a secondary drive on my ubuntu box. 

once plugged in, the drive shows up under BIOS, and under system>preferences>device manager. but it doesn't show up under the gnome partition editor.

i only have two HD* devices in my /dev. one is hdb, and the other is hdc. (i only have the new hard drive, and my ide cdrom plugged in)

"fdisk /dev/hdb" returns 'unable to open /dev/hdb'
"sudo fdisk/dev/hdb" returns 'unable to read /dev/hdb'

hdc is the cdrom drive. so... i'm stuck. anyone have step-by-step instructions somewhere?

---

### Post by Ek0nomik on 2007-06-11
What does:

```
sudo fdisk -l
```

and

```
sudo mount
```

and 

```
cat /etc/fstab
```

output?

---

### Post by ijason on 2007-06-11
ok, i found some help elsewhere and i've managed to get the hard drive formatted successfully. now it's just on to mount it and update the fstab.

thanks for you responce, though

:D

---

### Post by Ek0nomik on 2007-06-11
> **ijason said:**
> ok, i found some help elsewhere and i've managed to get the hard drive formatted successfully. now it's just on to mount it and update the fstab.

thanks for you responce, though

:D

Could you provide the link to where you figured it out?  I am curious, and someone in the future may stumble across this thread looking for a solution.  :)

---

### Post by ijason on 2007-08-27
the problem was that the IDE controller on the computer was fouled. i tested this by trying a different drive i knew to work on the same channel, and then the other. for some reason IDE0 didn't want anything other than the cd drive on it. IDE1 was happy to help.

---

