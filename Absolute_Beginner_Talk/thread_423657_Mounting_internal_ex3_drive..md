---
title: "Mounting internal ex3 drive."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-04-26
Okay, I recently formatted my NTFS drive to a ex3 drive. This is my fstab

```
/dev/sdb1       /media/hd2     ext3 user    defaults        0       2
```

It is appearing in /media/hd2 but it shows up as a folder with 75gb free space, not a drive?


Also, I do not have write privileges.

---

### Post by igknighted on 2007-04-26
you have seven columns, and fstab should only have 6.  You need to put a comma between user and defaults, like this:

```
/dev/sdb1       /media/hd2     ext3     user,defaults        0   2
```

Also, in linux drives are mounted as folders.  This is normal.

---

### Post by auraithx on 2007-04-26
I still don't have write permissions.

but that made it show up on the desktop, cheers.

---

### Post by kditty on 2007-04-26
i had the same problem yesterday here: [http://ubuntuforums.org/showthread.php?t=422877](http://ubuntuforums.org/showthread.php?t=422877)

that helped install the drive, and then i had to right click the drive and set it to read write access. check out the last two posts on that thread

---

### Post by auraithx on 2007-04-26
^ It won't let me change the permissions through the properties window.

---

### Post by igknighted on 2007-04-26
try:
```
sudo chown <your_username> /media/hd2
chmod +r+w /media/hd2
```

Or, change user,defaults to user,defaults,rw in the fstab

Try the second solution first, its the better way.

---

### Post by auraithx on 2007-04-26
cheers that fixed it

---

