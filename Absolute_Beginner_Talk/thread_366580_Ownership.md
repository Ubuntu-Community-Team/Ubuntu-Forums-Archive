---
title: "Ownership"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-02-21
You know how "Owner" in the file info is set to a specific user or root and only these 2 can access it?  How do I set the ownership to something that anyone can access it?

---

### Post by yabbadabbadont on 2007-02-21
You don't change the owner or group usually for that.  If you want everyone to be able to access it, you change it's permissions.

Assuming it is a file:

chmod a+r filename              -- this gives everyone permission to read the file.
chmod a+w filename             -- this gives everyone permission to write to the file.
chmod a+x filename              -- this gives everyone permission to execute the file, which means that the file would have to be a program or script of some kind.

---

### Post by nereid on 2007-02-21
You can set the owner and the group of a file and you can set the permissions for a file.

```

chown owner:group testfile

```

Sets the owner to *owner* and the group to *group*. You have three permissions per setting and per file. This means you can set read, write and execute for the owner, the group and the world (everybody else). The number 4 is read, number 2 is write and number 1 is execute. Combine these numbers to get the desired permission. For example 6 means read and write but no execute (4+2). 7 is everything (4+2+1) and 4 is read only.

```

chmod 666 testfile

```

This means that everybody is allowed to read and write to the file. The first 6 is for the owner, the second 6 is for the group and the last 6 is for the world. The following example is the default configuration for a new file: *664*. Which means owner and group can read and write but world can only read the file.

Hope I could help you there.

---

### Post by mcduck on 2007-02-21
..and before you do it, do not change ownership or rights of any files or directories outside your home directory, unless you really know what you are doing.

---

