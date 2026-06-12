---
title: "HELP error HDD..."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-06-12
/dev/sda1 already mounted or /media/disk-1 busy
i NEED to get to this hdd.i dont know if its dead or something but i need to try.
fresh install of ubuntu and i says the above error:S
running 7.0.4 fiesty fox...
whats wrong.how can i get it to mount and use it ?
please help i'm worried its dead:\
everything else is mounted automatically fine:\

---

### Post by taurus on 2007-06-12
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by keef247 on 2007-06-12
dunno whats happened but a restart seems to have made it work oh and i changed the sata cables the other way round. doubt that made any difference but no worries problem solved.cheers anyway.

---

