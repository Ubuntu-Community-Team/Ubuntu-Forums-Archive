---
title: "How do I remove a broken link/shortcut from the desktop?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-08-21
had a few shortcuts to folders/files on my Xubuntu desktop, but for some reason they are now broken. I can not delete them and right clicking also does not give me a delet option. any sugestions?

---

### Post by Seti on 2007-08-21
cd /home/~/you/Desktop

ls should show you what's there

rm to remove what you don't want on there

---

### Post by Ek0nomik on 2007-08-21
Did you create the shortcuts as root (by using sudo)?

As the previous poster mentioned:

```
cd /home/name/Desktop
ls -la #This allows you to see hidden files and permissions of all files
rm filename
sudo rm filename #Use this if the file is owned by root
```

---

