---
title: "External Hard Disk NTFS"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-08
ihave this external hard disk taht is all NTFS format, and it said it's read-only, how can i change that?

---

### Post by mtn on 2006-09-08
EDIT: Sorry, is NTFS, think that is read only in Linux! Someone else might be able to help though. Had a couple of beers and not paying attention! Shouldn't drink and Linux!

try

```
gksudo nautilus
```

in the terminal – Applications>Accessories>Terminal. This should open Nautilus file explorer in root mode. You might be able to change the properties on the hard disk to allow your normal login user to access the drive.

Hope this helps.

---

### Post by orb9220 on 2006-09-08
Well there is an experimental program called ntfs-3g that will allow writing.

But most people set up data drives as fat32 so linux and xp can read and write to them.

I was able after defrag it and using partition magic 8 in windows to convert my 112GB to fat32 from ntfs. But read this is not always succesful.

---

### Post by Devile on 2006-09-08
ok well maybe i'll copy it all back to a windows machine off of the drive, then re partition it as fat32 then put it all back on... but then it'll work???????

---

### Post by mgpower0 on 2006-09-08
it should work, I did exactly that with my 273 G external drive, but I just saved all the files to a folder in my home directory of Ubuntu then used gparted on the live cd to reformat to fat32. It shows as being a 273G fat32 drive now with all 273G available so seems to have worked fine.

---

