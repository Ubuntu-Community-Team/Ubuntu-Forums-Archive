---
title: "Dual-OS file-sharing?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-02-02
I've got part of my HD dedicated to Dreamlinux and the rest to Ubuntu. The Dreamlinux partition is formatted as Ext2, and Ubuntu is Ext3. Is there a way for me to browse and run files from one OS on the other?

---

### Post by bodhi.zazen on 2007-02-02
Mounting and permissions depends on the file system:

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by xpod on 2007-02-02
This should still apply to the partition you wish to mount.

[http://www.psychocats.net/ubuntu/mountwinhttp://www.psychocats.net/ubuntu/mountwindowsdows](http://www.psychocats.net/ubuntu/mountwinhttp://www.psychocats.net/ubuntu/mountwindowsdows)

Just look for the details of your ext partition with the "sudo fdisk -l"command instead of windows and call the directory you make for it something other than windows obviously.:) 

If you want it mounted so it appears on your desktop i believe making the directory in "/media" will do that for you....."sudo mkdir /media/dreamlinux" for example

Thats what i follow myself m8 as i`m forever forgetting.

EDIT:Grrrrrrr:-)
EDIT2:you do it so much better than me anyway m8

---

### Post by kbsuperstar on 2007-02-02
Thanks, i'll have to try it out

---

