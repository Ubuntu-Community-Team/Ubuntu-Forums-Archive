---
title: "how to mount an fat32 partition? [Resolved]"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by nightwolf2k5 on 2006-12-03
hey everyone.. i just made a new fat32 partition in my hdd so that i can access that partition via winxp and ubuntu..

the problem is.. i just made the patition and now i have no clue what to do in ubuntu..
i kinda did what i would do to mount my ntfs patition..
made a new directory in media
then edited the fstab file and did what i would do with the ntfs partition.. except.. it then said fat32 is an ivalid file system (when i put mount -a)

then.. ah.. kinda used this command
```
sudo mount -t auto /dev/sda7 /media/share
```

now.. i can see the partition.. but.. i dont have write permission in it..

what do i do? please help ya'll.. ](*,) ](*,)

---

### Post by aysiu on 2006-12-03
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

### Post by nightwolf2k5 on 2006-12-03
sorry man.. unfortunately.. thats for the mounting of ntfs partitions man..

i kinda wanna mount my fat32 partition and make it write enabled..

thanks though :)

---

### Post by Hankers on 2006-12-03
Just scroll down a bit. It's for both NTFS and FAT32

---

### Post by nightwolf2k5 on 2006-12-03
dude.. i did that.. now.. i can see the fat partition without any problem.. but.. i still dont have write permission.. it says cannot change permission for drive.. :(

---

### Post by taurus on 2006-12-03
> **nightwolf2k5 said:**
> dude.. i did that.. now.. i can see the fat partition without any problem.. but.. i still dont have write permission.. it says cannot change permission for drive.. :(
Paste your /etc/fstab here then!!!

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by nightwolf2k5 on 2006-12-03
sorry man.. it works now.. just needed a restart.. :)

thank ya'll so much for ur help man! :)

---

