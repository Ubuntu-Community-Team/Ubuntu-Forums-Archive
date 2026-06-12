---
title: "I think i need to be root"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by bookworm666 on 2007-06-24
Quick out line.

I need to modify an iso file. I need to delete a couple of files and add new ones. file roller will open the iso file but it says it's owned by root and there for read only.

may be the program can't modify it even in root, I don't know that either. as anyone any ideas.

thanks for any help

bookworm666

---

### Post by 5-HT on 2007-06-24
To lauch file-foller and edit the archive with root privs:
```
gksudo file-roller path_to_iso
```For further reference: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
cheers,

---

### Post by kecci on 2007-06-24
You can become root in Ubuntu by opening up a terminal and typing "sudo -s".
Or you can press "Alt+F2" and type "gksudo" and the name of the application you want to run as root.

---

