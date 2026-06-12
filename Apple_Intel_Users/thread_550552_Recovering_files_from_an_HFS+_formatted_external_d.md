---
title: "Recovering files from an HFS+ formatted external drive... withouth a Mac"
date: 2007-09-14
forum: Apple Intel Users
---

### Post by Roger Mudd on 2007-09-14
Long story short...

[LIST]
[*]Purchased an iMac
[*]Said iMac had a faulty video card which necessitated return (not exchange - I will not have a Mac to access these files)
[*]Before returning, I backed up all data to two HFS+ formatted external drives (probably a mistake in choosing that file system)
[*]I'm running Feisty on my Thinkpad
[*]The drives mount fine and I can read the contents from the Thinkpad
[*]However, I cannot access some protected *User* directories and I cannot copy any protected files
[/LIST]

How would I go about pulling the files off the external drives and copying them to the Thinkpad? Seems like I need to change the permissions, but I don't know how to or if this is even possible. any assistance is greatly appreciated.

---

### Post by alephsmith on 2007-09-14
Have you used [FONT="Courier New"]chown[/FONT]?

this program is used to _ch_ange _own_er of a file

more specifically

```
 sudo chown /your/file/path
```

---

### Post by cyberdork33 on 2007-09-14
Linux recognizes the permissions settings in HFS+, thus those files are all owned by "another user". You can access them as root, and change the permissions to your heart's delight, just be careful about changing permissions if you plan to copy all those files back to your Mac.

---

