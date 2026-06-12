---
title: "Mv Command Troubles!"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by wdbreen on 2006-06-09
Gday All,
I'm having troubles using the *mv* command to force a directory from /home to /etc
The trouble is that a directory of the same name exists but i want to overwrite it?

I have used mv -f but that doesnt work.

Help

---

### Post by BaffledMollusc on 2006-06-09
[QUOTE=wdbreen]Gday All,
I'm having troubles using the *mv* command to force a directory from /home to /etc
The trouble is that a directory of the same name exists but i want to overwrite it?

I have used mv -f but that doesnt work.

Help[/QUOTE]
You should be able to do that. The problem may be that you (as a normal user) don't have permissions to write to the /etc directory. In fact, you don't have permission to write to any directory outside your home directory.

To get around this, add "sudo" to the beginning of your terminal command, e.g. "sudo mv test.txt /etc/test.txt". 

sudo means execute this command as an administrator. This will give you permission to do anything you want; make sure you know what you're doing :)

---

