---
title: "MacOSX message"
date: 2007-05-24
forum: Apple PPC Users
---

### Post by harald ornstein on 2007-05-24
I have Edgy in dualboot with macosx. Every time I enter macosx there is a screen saying:" macosx does'nt recognize the disk with ubuntu, what shall I do ? initalize, ignore or remove ?"
How can I get rid of this window?

---

### Post by onbongos on 2007-05-24
install ext2fsx so the drive mounts

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

---

### Post by Auria on 2007-05-24
> **onbongos said:**
> install ext2fsx so the drive mounts

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

I would advise against doing that [without backups and knowing you take a risk]. extfs caused me kernel panics and corrupted my ubuntu partition.

---

### Post by stmiller on 2007-05-24
I use that ext2 driver. But I specify in the system prefs in OS X for it to be read only. That is safe, and you cannot do any harm if you use that setting.

---

### Post by Auria on 2007-05-25
> **stmiller said:**
> I use that ext2 driver. But I specify in the system prefs in OS X for it to be read only. That is safe, and you cannot do any harm if you use that setting.

well the time it corrupteds my ubuntu partition, it was in read-write mode true, though even in read-only mode it caused OS X kernel panics...

well anyway perhaps it's my configuration, but it does look unstable

---

