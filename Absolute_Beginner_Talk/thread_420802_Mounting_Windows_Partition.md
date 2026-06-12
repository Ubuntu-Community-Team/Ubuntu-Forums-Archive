---
title: "Mounting Windows Partition"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-23
My windows partition mounts automatically when I login in, but the icon for that partition is on both the Desktop and under "Computer". How can I prevent the icon from showing up on the Desktop?

---

### Post by Patrick K on 2007-04-24
Open Configuration Editor (System Tools). Go to apps>nautilus>desktop. There is an option for volumes_visible. Clear the check.

---

### Post by noorez on 2007-04-24
Ok...that works...but I noticed something strange about that...
The "Filesystem" icon does not show up on the Desktop even though its a mounted file system...

And also...what are the configuration files that the Configuration Editor is changing?

---

### Post by Patrick K on 2007-04-24
I don't know the answer to either question so I'll bump you up.

---

### Post by mikewhatever on 2007-04-24
The actual files are in the hidden .gconf directory in your home folder. You can un-hide the hidden folders with Ctrl+H combination.

---

