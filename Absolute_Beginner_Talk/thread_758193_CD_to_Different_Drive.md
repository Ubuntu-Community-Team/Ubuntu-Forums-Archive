---
title: "CD to Different Drive?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by dalezjc on 2008-04-17
When using the terminal, how do I change to a different drive?  I tried:

cd drivename, but that didn't work.

Thanks,
Dale

---

### Post by unutbu on 2008-04-17
'Drives' like C:, D:, E:, etc don't exist in linux. Instead, partitions are 'mounted' at directory locations that you can control in /etc/fstab.

So the first question you need to answer is, are your drives (partitions) mounted?

You can answer that with
```

mount
``` which should return something like

```

% mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
/dev/sdb1 on /media/disk type ext3 (rw)

```

/dev/sda1 is the first partition (indicated by the 1) on the first physical drive.
/dev/sdb1 is the first partition on the second physical drive. 

So whereas in windows you would do

```
cd d:
```

in linux you do something like
```

cd /media/disk
```

Hope this helps.

---

### Post by aktiwers on 2008-04-17
all your discs are in /media/

So "cd" to there and type "ls"

It should list all your drives. Then cd to the drive you want.

Alternativly you can type "cd" and drag/drop the drive into the terminal, it will type the path for you.
Edit: Forget the last part.. only works for files and folders (not the drives on harddisc)

You could go with your filebrowser though aslo.. and hit "CTRL+L" to see the path.

---

### Post by dalezjc on 2008-04-17
Thanks guys!

Dale

---

