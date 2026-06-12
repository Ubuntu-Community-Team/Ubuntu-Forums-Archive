---
title: "Backing up file"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by laforge on 2007-08-23
Ok, I need to reinstall, too much stuff on this one but I want to back up everthing first.  I am having problems though.  I connected up and external USB HDD but I can't move files into it.  When I try to drag and drop the files I get a permission error and when I try mv the directory I am trying to move only gets renamed.

If there is a way to sudo move things or just write it all to a DVD that would be great.

Thanks for any help in advance.

---

### Post by Jimmyfj on 2007-08-23
> **laforge said:**
> Ok, I need to reinstall, too much stuff on this one but I want to back up everthing first.  I am having problems though.  I connected up and external USB HDD but I can't move files into it.  When I try to drag and drop the files I get a permission error and when I try mv the directory I am trying to move only gets renamed.

If there is a way to sudo move things or just write it all to a DVD that would be great.

Thanks for any help in advance.

You could try: **gksu nautilus**, this will give you root access through Nautilus.

---

### Post by por100pre1 on 2007-08-23
Use Grsync to backup to your ext HDD. Run it with sudo if needed. Untick the **preserve permissions** option for better results. Hope this helps. :)

---

### Post by laforge on 2007-08-24
Thanks very much guys.

---

