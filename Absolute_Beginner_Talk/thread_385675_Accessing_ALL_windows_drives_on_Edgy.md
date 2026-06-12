---
title: "Accessing ALL windows drives on Edgy"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Fataltragedy2 on 2007-03-16
Hello,

I've got my C: Drive to show up by mounting, but how do I do the same for my D: and E: drives?

I'll appreciate it alot if you can help!

---

### Post by Belyel on 2007-03-16
There is more than one way to do this.  Did you manually mount your C:\ drive or did Linux find it and mount it for you?  Regardless, the way to manually mount a drive is to use the command ```
mount -t *filesystem* -o umask=000 *pathtodrive* *foldertomountto*
```

I expect that looks greek to you if you haven't seen it before.  So, for example, if I wanted to mount a drive located at /dev/hdb1 (an IDE slave, partition 1), which is formatted ntfs to a folder in /media/movies, I would phrase the command:
```
 sudo mount -t ntfs -o umask=000 /dev/hdb1 /media/movies
```

If this works out just fine, then you can edit (after backing up) the file /etc/fstab so the drives will mount every time you boot linux (edit as root).  The format is a little different in fstab, the syntax is ```
*/dev/drive*     *foldertomountto*     *filesystem*    user,umask=000    0    0 
```

Also, you can look at the man page for the mount command by typing "man mount" at the command prompt for more examples and options for mounting drives.

hope this helps.  You can also search the forums for more help as needed.

---

