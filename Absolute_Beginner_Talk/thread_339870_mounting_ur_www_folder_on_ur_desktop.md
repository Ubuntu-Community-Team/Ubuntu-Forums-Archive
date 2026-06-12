---
title: "mounting ur www folder on ur desktop"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by docetes on 2007-01-16
how wud i mount the www folder in var to my desktop

---

### Post by docetes on 2007-01-16
i've got further but i'm stuck here

sudo mount /var/www/ /home/docetes/www/

mount: you must specify the filesystem type

what file system do i stick in?

---

### Post by mcduck on 2007-01-16
You don't mount it, you link it :)

'ln -s /var/www ~/Desktop'

---

### Post by docetes on 2007-01-16
that worked great thx. how remove that now?

---

### Post by docetes on 2007-01-16
sorry another quick question it is now telling me that all the files www on my desktop are read only how will i change that?

---

### Post by mcduck on 2007-01-16
You can remove the link just like any other file on your desktop. And permissions are what they are in /var/www. I suppose you could run 'sudo chmod a+rw /var/www' to make it read/write for everybody, although I bet that's not a wise thing to do when you run a web server..

---

### Post by punx45 on 2007-01-16
yeah, thats a bad idea.

i changed the group of /var/www from root to my username, and enabled group write access.

```
sudo chown :<your username> /var/www
```
will change the group of /var/www from root to your username

then 
```
sudo chmod g+w /var/www
```
will give the group "your username" write permissions to /var/www   if you have already created subdirectories as root, you might need to change them also.

check out the [wiki on permissions]("https://help.ubuntu.com/community/FilePermissions") for more detailed info.

---

