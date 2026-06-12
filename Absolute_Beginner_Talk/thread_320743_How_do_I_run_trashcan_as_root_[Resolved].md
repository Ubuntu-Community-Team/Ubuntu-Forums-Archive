---
title: "How do I run trashcan as root [Resolved]"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-17
How do I run the trashcan as root? I have two folders in there that refuse to be deleted, and I can't seem to get in there as root.

---

### Post by benuski on 2006-12-17
try doing:

```
sudo rm -r "filepath"
``` 
That will remove all of the files and then remove all of the directories their in.  But don't use quotes, just put the directory path in there.

---

### Post by scrooge_74 on 2006-12-17
try opening a terminal window and then type sudo nautilus, that way you have nautilus with root powers

---

### Post by aysiu on 2006-12-17
```
gksudo nautilus
``` Then go to /root/.Trash

---

### Post by aysiu on 2006-12-17
> **benuski said:**
> try doing:

```
sudo rm -r "filepath"
``` 
That will remove all of the files and then remove all of the directories their in.  But don't use quotes, just put the directory path in there.
This command can be **very** dangerous. I think the terminal is way too powerful to be using *sudo rm -r* anything...

---

### Post by foxmulder881 on 2006-12-17
Try deleting while holding down then SHIFT key. It'll bypass the trash can but should remove them permanantly.

---

### Post by Pobega on 2006-12-17
Thanks, that worked. I just moved everything into my /home/user folder and deleted it.

/root/.trash or /root/.Trash doesn't exist, nothing of the like does.

---

### Post by aysiu on 2006-12-17
> **Pobega said:**
> Thanks, that worked. I just moved everything into my /home/user folder and deleted it.

/root/.trash or /root/.Trash doesn't exist, nothing of the like does.
All the folders starting with a . are hidden folders, including /root/.Trash

I guess I should have told you to go /root and then press Control-H, but if you type ```
/root/.Trash
``` in the location bar, it should take you there.

---

### Post by scrooge_74 on 2006-12-17
yes it exist it is just that your normal user can't see it

cd /root
ls -l -a

---

### Post by Pobega on 2006-12-17
Edit: Nevermind

---

