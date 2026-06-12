---
title: "Cannot change permissions 'Not owner of this file'"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by DrBobert on 2006-08-04
OK, I've read the notes on this and as I understand it, the default user that is created at installation has automatic control over file permissions.

Well, I don't. And I need to in order for Firefox extensions to work properly.

(I have 5.10)

Once again, I apologise if I'm being worse than a n00b.

---

### Post by aysiu on 2006-08-04
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

But you shouldn't need to modify system files to install Firefox extensions. Close Firefox. Paste this command into the terminal: ```
sudo chown -R bobert:bobert /home/bobert/.mozilla
``` Then restart Firefox and install extensions to your heart's content.

If that doesn't work, go to the address bar and type ```
about:config
``` Then in the **Filter** bar, type ```
xpinstall.enabled
``` Make sure it's **true**.

---

### Post by steve.horsley on 2006-08-04
No, it is user **root** who has full administrative rights to the machine. The first user has the ability to temporarily assume those rights by preceding his connands with **sudo** and then giving his password again. 

As Aysiu says, you shouldn't need to use sudo to install extensions to firefox because they go in your home folder.

---

