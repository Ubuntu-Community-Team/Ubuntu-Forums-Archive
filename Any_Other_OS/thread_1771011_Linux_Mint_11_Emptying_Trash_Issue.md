---
title: "Linux Mint 11 Emptying Trash Issue"
date: 2011-05-29
forum: Any Other OS
---

### Post by manuleka on 2011-05-29
I deleted a VM folder (which has contents in it) and are all in Trash, but when i try empting it, System wouldn't let me.
I get the following Errors:
```

Error while deleting
There was an Error while deleting VirtualBox VMs
Detail:
Failed to delete the item from the trash 

```

i have tried running Nautilus as root but i can't get to Trash

help please...

---

### Post by Perfect Storm on 2011-05-29
Moved to Other OS/Distro Talk.

---

### Post by sffvba[e0rt on 2011-05-30
OK... open Nautilus again as root and then hit Ctrl + L and type in "trash:///" (without the quotation marks)... also make sure that you can view hidden files, hit Ctrl + H...

Might help to make sure you are not still running any VM software that has a lock on the files...


404

---

