---
title: "Changing File Permissions"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-03
I've found some info on Chmod, but my question is

How do I apply the same set of permissions to all decendants (files or folders) of a folder to the same permission set?

In mycase I have \home\share\music
The structure under that is \artist\album\song.mp3
I want to grant all users full permissions to everything under \home\share\music

Chmod looks like the way to go, but I'm unsure of the synthax?

Follow-on Qustion - can I set anything on the parent folder (\home\share\music) such that any new objects created under it "inherit" its permissions automatically?

Thanks

---

### Post by DannyG on 2006-12-03
use the -R argument. R = recursive, such that is recursively applies the chmod command to all subfolders and files.
```

chmod -R 777 /home/share/music
```

Would grant all users full and unrestricted access to your music folder and everything in it. Obviously you want to replace 777 with the level of permission you want to give.

---

### Post by LLRNR on 2006-12-03
Yes, you can change permissions recursively by using the **-R** switch.

So, if you want to grant read and write access to all users on your /home/dkenny/share/music folder, you'd do something like:
```
cd ~/share   
chmod -Rv ugo+rw music
```
The **-v** switch is for verbose output.
~ means /home/yourusername

For more info, see either **chmod --help** either **man chmod**.

Cheers,

LLRNR

---

### Post by dkenny on 2006-12-03
Cool, that worked.

Any ideas on the "inheritance" possiblility?

---

