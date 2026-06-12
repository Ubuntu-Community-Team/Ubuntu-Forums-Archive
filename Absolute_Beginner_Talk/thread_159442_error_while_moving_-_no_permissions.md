---
title: "error while moving - no permissions"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Jordan Meeter on 2006-04-12
I'm trying to delete a folder "mov" in /home/jordan/.azureus/torrents/ and this message pops up

"Error while moving
Cannot move "/home/jord...rrents/mov" to the wastebasket because you do not have permissions to change it or its parent folder."

How do I *get* permissions?

---

### Post by taurus on 2006-04-12
[QUOTE=Jordan Meeter]I'm trying to delete a folder "mov" in /home/jordan/.azureus/torrents/ and this message pops up

"Error while moving
Cannot move "/home/jord...rrents/mov" to the wastebasket because you do not have permissions to change it or its parent folder."

How do I *get* permissions?[/QUOTE]
Try (from a terminal...)
```

sudo rm -rf /home/jordan/.azureus/torrents/mov

```

---

### Post by Jordan Meeter on 2006-04-12
Cool, that worked. But why don't I have the permissions to do it via file browser? I am the administrator?

---

### Post by taurus on 2006-04-12
Normally, you have permission to do whatever you want with files and directories in your home directory.  Not sure why you couldn't remove it though.  However, "sudo" can remove everything so be extra careful with "sudo rm -rf" command, okay!  ;)

---

### Post by Jordan Meeter on 2006-04-14
What are the other commands for moving, copy, deleting, etc?

---

### Post by 1derphull on 2006-04-23
[QUOTE=Jordan Meeter]What are the other commands for moving, copy, deleting, etc?[/QUOTE]

This may help 

[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

### Post by enopepsoo on 2006-04-23
[QUOTE=Jordan Meeter]What are the other commands for moving, copy, deleting, etc?[/QUOTE]

mv moves files
cp copies files
mkdir mnakes a directory

---

