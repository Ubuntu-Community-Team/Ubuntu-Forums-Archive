---
title: "Files with a space in the name"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by caoinan on 2007-08-26
um yes I just started using ubuntu and im trying to change the permissions of some of my external harddrive so I can add, and delete things so I know i just need to change the owner or the permissions but I have a 1 terabyte My Book and it has a space in the name so I cant access it from my terminal can someone tell me how to access things from the terminal with a space in the name please.

---

### Post by Majorix on 2007-08-26
Just  quote the name. Like "My Book".

---

### Post by asmoore82 on 2007-08-26
indeed...
either encase the whole string in quotes ...
```
~ $ cd "/mnt/windoze/Documents and Settings"
```

-OR- **backslash escape** the spaces to protect them from the **shell**...
```
~ $ cd /mnt/windoze/Documents\ and\ Settings
```

the most important thing to take away from this "names with spaces" situation is that
the TAB key is your Best Friend :KS

pressing TAB at any time on the BASH CLI will cause it to complete names for you as much as possible.
pressing TAB even more will make it show you a list of available choices when an exact match can't be made.

---

### Post by asmoore82 on 2007-08-26
> **caoinan said:**
> um yes I just started using ubuntu and im trying to c**hange the permissions of some of my external harddrive so I can add, and delete things so I know i just need to change the owner or the permissions** but I have a 1 terabyte My Book and it has a space in the name so I cant access it from my terminal can someone tell me how to access things from the terminal with a space in the name please.

the ntfs-3g drivers are required to write changes to NTFS volumes ...
also even then NTFS and FAT are not UNIX filesystems and cannot properly maintain
UNIX file ownership and permissions.

---

### Post by caoinan on 2007-08-27
Thanks for help but now I have another question: how do I change the permissions and owner of external hard drives or directories to read-write?
Also what is the difference in showing the hard drive as a directory in the media -File Browser and showing it as hardware in the Computer-File Browser
and if I change ones owner and permissions will it change the other or do I have it change it there too?

---

