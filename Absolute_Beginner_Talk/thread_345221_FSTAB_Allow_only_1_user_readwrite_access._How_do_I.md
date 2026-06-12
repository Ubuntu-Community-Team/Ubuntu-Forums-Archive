---
title: "FSTAB: Allow only 1 user read/write access. How do I do that?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by C-A on 2007-01-24
I have three mounted windows partitions. Currently all users have read / write access to them. I have three users on my pc and want to allow only one user (me) to have read / write access to the partitions.

From what I have read, there are two options for controlling read / write access when editing the fstab which are user and root. I don't want to allow only root access because this would limit my access. 

Is there another option?

Thanks in advance for any help / ideas.

---

### Post by yabbadabbadont on 2007-01-24
```
/home/bubba $ cat /etc/fstab | grep windows
/dev/hda1        /windows         vfat          noauto,user,quiet,utf8,umask=007,gid=46  0       0

```
In my case, the group (gid) has been set to plugdev.  There is also a uid option that you can use to set the owner.  You would also need to adjust the umask value so that only your user and group has access.  "man mount" for details on the options available when mounting fat and vfat partitions.  (vfat can use the fat options as well as it's own)

---

### Post by Canis familiaris on 2007-01-24
Follow this Link on mounting and sharing Windows Partitions:
[http://ubuntuforums.org/showpost.php?p=2052209&postcount=6]("http://ubuntuforums.org/showpost.php?p=2052209&postcount=6")

---

### Post by C-A on 2007-01-24
Here is an entry in my fstab:

# /dev/hdc1
UUID=70D3-4BDA  /media/hdc1     vfat
defaults,utf8,umask=007,gid=46 0       1

This entry was automated with my edgy install and looks different in the beginning (# /dev/hdc1
UUID=70D3-4BDA ) than what I am used to.

Anyway, do I just change gid=46 to gid=my-user-name and add uid=my-user-name?

---

### Post by C-A on 2007-01-24
I was not sure about how to make the above changes so I created a separate group that could have access to the mounted drives, added myself to the group, and used the gid in my fstab entry. Not sure if this is the best way but it seems to work so far.

---

