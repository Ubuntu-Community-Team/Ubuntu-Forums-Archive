---
title: "Deleted files on ntfs drives doesn't move to trash!"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by paranoid_humanoid on 2008-03-29
i share a hard drive with windows xp. all of my partitions are ntfs except for the one with ubuntu on it, it's ext3..

when i delete a file from my ext3 partitions it goes to the trash.. when i delete a file from any of the other partitions, it just *pouff* disappears.. not .trash folders or anything...

why is that?

---

### Post by dcstar on 2008-03-29
> **paranoid_humanoid said:**
> i share a hard drive with windows xp. all of my partitions are ntfs except for the one with ubuntu on it, it's ext3..

when i delete a file from my ext3 partitions it goes to the trash.. when i delete a file from any of the other partitions, it just *pouff* disappears.. not .trash folders or anything...

why is that?

Because they are not native Linux filesystems - NTFS is a Windows filesystem.

---

### Post by someone here on 2008-04-03
I have the same problem
is there any way to get the file back
the file itself isn't deleted cause no space is freed, which means the file is still there..

---

### Post by someone here on 2008-04-03
I forgot to mention I checked the trash and nothing was there

---

### Post by Tteddo on 2008-04-03
If you look on the ntfs volume, there will be a trash folder called .Trash-username (mine is .Trash-tteddo) and that's where Ubuntu puts your deleted files on that volume. It will do it other volumes also.
It is a hidden folder, so you will have to Show Hidden Files to see it.

---

### Post by lswest on 2008-04-03
Or, it may be, that if it's mounted with sudo, the files will go to the .Trash in /root

---

