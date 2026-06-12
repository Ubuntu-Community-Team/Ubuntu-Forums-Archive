---
title: "mount ext3 partition with read/write permission for all"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by hezral on 2006-05-25
hi im trying to mount a ext3 partition so that all user and not root only can have read/write permission. what is the line to put in fstab? i tried it like this but didnt work

/dev/hda4 /media/hda4 ext3 defaults 0 0

any help? thanks

---

### Post by joshrobinson on 2006-05-25
[QUOTE=hezral]hi im trying to mount a ext3 partition so that all user and not root only can have read/write permission. what is the line to put in fstab? i tried it like this but didnt work

/dev/hda4 /media/hda4 ext3 defaults 0 0

any help? thanks[/QUOTE]


try


/dev/hda4 /media/hda4 ext3 defaults,umask=0000 0 0

then unmount and remount and try again

sudo umount /dev/hda4
sudo mount /dev/hda4

---

### Post by aysiu on 2006-05-25
This line is fine as is: ```
/dev/hda4 /media/hda4 ext3 defaults 0 0
``` Just paste these two commands into terminal: ```
sudo chown -R hezral:hezral /media/hda4
sudo chmod -R 777 /media/hda4
```

---

### Post by joshrobinson on 2006-05-25
[QUOTE=aysiu]This line is fine as is: ```
/dev/hda4 /media/hda4 ext3 defaults 0 0
``` Just paste these two commands into terminal: ```
sudo chown -R hezral:hezral /media/hda4
sudo chmod -R 777 /media/hda4
```[/QUOTE]

i always forget the chmod numbers.. nice job aysiu

---

### Post by hezral on 2006-05-25
thanks i'll try that. what does hezral:hezral stands for? group/user?

---

### Post by aysiu on 2006-05-25
[QUOTE=hezral]thanks i'll try that. what does hezral:hezral stands for? group/user?[/QUOTE] Close--user:group.

It's changing ownership of the partition to you.

777 lets everyone read/write/execute

---

### Post by hezral on 2006-05-26
thanks. i already had a work around for it b4 but i was trying to get the right fix for the fstab.

---

### Post by FaceLeg on 2007-03-10
Thanks!  I had this problem too, all fixed now.

---

