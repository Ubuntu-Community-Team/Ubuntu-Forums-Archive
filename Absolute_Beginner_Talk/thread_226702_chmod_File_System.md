---
title: "chmod File System"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by alainsamoun on 2006-07-31
How do you change the permission in the file system from the Terminal?
i.e. I want to edit /etc/apache2/mods-available/userdir.conf

---

### Post by aysiu on 2006-07-31
*chmod*ing system files is a quick way to render your system unusable.

Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Tomosaur on 2006-07-31
This is the reason we have the sudo command.

If you want to edit an otherwise inaccessible file, you should use sudo. In your case then, try this:

```

sudo nano /etc/apache2/mods-available/userdir.conf

```

If, however, you want to use a gui editor, such as gedit, you should use 'gksudo' instead of 'sudo'.

---

