---
title: "unmount..how do i"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-05
hi i used 

gksudo gedit  /etc/fstab
 
and added >       /dev/hda1     /media/shared    ext3   defaults  0   1
 to my fstab and saved
 
then  >sudo mkdir /media/shared
sudo mount -a
sudo chmod -R 777 media/shared

 i used these commands to mount  hda1 on dev/media/shared
 
my question is what is the command to unmount this

i have clicked on unmount but it says i dont have permission to unmount

---

### Post by M_the_C on 2007-01-05
Forget what I said.

Follow below instructions.

---

### Post by louistan3 on 2007-01-05
hey...

i think its

```
sudo umount /media/shared
```

hope it works.. i dont use it much myself...but you could find more options if you look at the man pages for umount...

:D

---

### Post by i++ on 2007-01-05
can you not just ```
sudo umount /dev/hda1/ -l
```

---

### Post by STREETURCHINE on 2007-01-05
thanks bit stupid of me i think i tried every command but the most obvious

 so thank you m_the_c,

---

