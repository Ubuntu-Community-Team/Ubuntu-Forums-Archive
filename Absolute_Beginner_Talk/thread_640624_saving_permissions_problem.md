---
title: "saving permissions problem"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-14
I've made some changes to apache2.conf but when I try to save them I get
Could not save the file /etc/apache2/apache2.conf.
It says I donot have permission even if nothing else is open.I am the only user.
What's happening

---

### Post by arochester on 2007-12-14
You need to use sudo to put you in root mode first e.g. sudo gedit (name of file)

---

### Post by The Cog on 2007-12-14
You need root permissions to edit files outside of your home directory. You get these by typing sudo (or gksudo for graphical apps) in front of the command that needs the extra rights, e.g.
**gksudo gedit /etc/apache2/apache2.conf**

Read this for more explanation:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gleble on 2007-12-14
sudo gedit etc/apache2/apache2.conf brings up the file but saving it gives 
Could not save the file /home/neil/etc/apache2/apache2.conf.
Unexpected error: File not found
The path is correct

---

### Post by saj0577 on 2007-12-14
> **gleble said:**
> sudo gedit etc/apache2/apache2.conf brings up the file but saving it gives 
Could not save the file /home/neil/etc/apache2/apache2.conf.
Unexpected error: File not found
The path is correct

As your saving a copy of it you should not need to use sudo as you are not editing it, you are saving a copy of it in your home folder and editing that.

Saj

---

### Post by gleble on 2007-12-14
> **gleble said:**
> sudo gedit etc/apache2/apache2.conf brings up the file but saving it gives 
Could not save the file /home/neil/etc/apache2/apache2.conf.
Unexpected error: File not found
The path is correct
I should have said editing and saving

---

### Post by saj0577 on 2007-12-15
As you are saving it in a directory which you have permissions to edit then you do not need to use sudo.

You would only need to use sudo if you were editing then saving it in a directory you do not have permissions for.

Saj

---

