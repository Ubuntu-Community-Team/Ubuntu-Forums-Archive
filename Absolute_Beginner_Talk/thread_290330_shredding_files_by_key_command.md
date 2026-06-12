---
title: "shredding files by key command"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-11-01
Hello, is it possible to introduce a new command (such as Ctrl+Del) which shreds a selected file in the gnome display manager instead of only deleting it with out doing this in the command line (shred -iterations=30 /etc/fstab)?

---

### Post by ciscosurfer on 2006-11-01
If you're using EXT3, this really isn't an issue as the journal is zeroed out everytime you delete a file, as far as I can remember.  But check me on that.

---

### Post by gagatz on 2006-11-01
Well then, are there any differing opinions on this?

---

### Post by ciscosurfer on 2006-11-01
gagatz,

After searching through my posts and the rest of the forum, I recalled information regarding 'shred' and 'wipe'.  You can check out the man pages on these by issuing **man shred** and **man wipe**.  Shred should already be on your system (/usr/bin/shred and is part of the coreutils package -- SELinux [security enhanced linux] coreutils, called policycoreutils, can be grabbed from the 'universe' repository).  Wipe can be installed via a quick **sudo aptitude install wipe** and then you can check the man page for it by typing in **man wipe**.  

For a little more on SELinux, [you can check here]("https://wiki.ubuntu.com/SELinux").

Hope that helps you out!

---

