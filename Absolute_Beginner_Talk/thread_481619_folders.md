---
title: "folders"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-22
I'm noticing that a select few folders have a pad lock on them. Means nothing to me, only that I have to quadruple click to get into them. Still i wonder why they do that? Do i have the option to password protect them? If so that could come in handy.

---

### Post by dbbolton on 2007-06-22
> **Ssj3_man said:**
> I'm noticing that a select few folders have a pad lock on them. Means nothing to me, only that I have to quadruple click to get into them. Still i wonder why they do that? Do i have the option to password protect them? If so that could come in handy.
the lock means that the folder is read-only or that the current user doesn't have full permissions for that folder. 

you can't add a password to a folder, afaik, but you can prevent other users from accessing it. right-click on the folder, then click Properties, then go to the Permissions tab. under "others", select "None".

---

### Post by steve0921 on 2007-06-22
If you're interested, you can do a quick google search about linux file permissions to find out much more. Roughly, every file and folder in linux had both a user that owns it and a group associated with it. The permissions then specify whether the file can be read, written to, or executed. Permissions are specified separately at three levels: what the file's owner is allowed to do, what members of the affiliated group are allowed to do, and what all other users are allowed to do. Typically only the owner will have write access, so files you don't own will be padlocked.

In addition to dbbolton's suggestion, if you want more users than just yourself to be able to access a file (or folder) and to exclude others you can make yourselves members of a new group and associate that group with the files. Then set the group level permissions so you can read and write, and block reading and/or writing by other users.

---

### Post by steve.horsley on 2007-06-22
The padlocks mean you don't have full rights in there - read only perhaps. 

If you need to write to one of these folders, you need to borrow root's proviledge. In command line, precede the command you want to use with the word sudo. e.g.
**sudo cp filename foldername**
It will ask you for your password again (the one you logged in with).
To use ghe GUI file manager, use Alt-F2 and enter the command:
**gksudo nautilus**
which gives you a file manager with full rights to the whole system. Be careful - it can delete your system too.

---

