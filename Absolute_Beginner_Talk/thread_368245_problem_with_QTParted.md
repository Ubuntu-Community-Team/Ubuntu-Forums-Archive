---
title: "problem with QTParted"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-02-23
I installed QTParted, but when I open it it tells me there are no devices and that perhaps I am not ROOT user. So I log in as root but the program does not exist in the ROOT applications-->system tools menu. Actually, the system tools menu does not even exist in the root users applications menu. I tried uninstalling then reinstalling it while logged in as root, but to no avail. Any ideas?

---

### Post by tgalati4 on 2007-02-23
I haven't used it, but QTParted is just a front-end to parted.  Try sudo parted in a terminal.  At the prompt type "print 1"  "print 2" "print 3"  "print 4" "quit"

This will determine if parted works properly and that you can see your partitions.

start qtparted from the terminal:  sudo qtparted &

If you log into the entire session as root, you won't have access to all the tools that you so carefully set up.

---

