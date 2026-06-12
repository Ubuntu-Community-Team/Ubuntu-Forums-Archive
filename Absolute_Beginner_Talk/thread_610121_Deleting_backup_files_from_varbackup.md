---
title: "Deleting backup files from var/backup"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by reklabunde on 2007-11-11
I'm new to Ubuntu (7.10).  How do I delete backup files from /var/backup?  :confused:

Thanks, Richard

---

### Post by metol on 2007-11-11
The backup files likely have root ownership & permissions.  One way to delete them would be to open a terminal window (Applications / Accessories / Terminal).  Then type...

```
cd /var/backup
```

then delete the files using sudo (this gives you root privileges)

```
sudo rm *filenametodelete*
```

---

### Post by mkoehler on 2007-11-11
In addition, if you are trying to delete folders as well, you'll want to include the 'recursive' option:

```
sudo rm -r <folder_to_delete>
```

Cheers!

---

### Post by reklabunde on 2007-11-11
Thank you!  I was able to delete the large folders/files.  Is there a way to get root ownership and permissions so that I don't have go use these terminal commands to remove individual files/folders, but instead just use a file browser?  ~Richard

---

### Post by mkoehler on 2007-11-11
A better choice would be to open up nautilus as root, by using the command ```
sudo nautilus
``` in the terminal.  Then you can carry out those operations graphically with root privileges.

---

### Post by metol on 2007-11-11
> **reklabunde said:**
> Thank you!  I was able to delete the large folders/files.  Is there a way to get root ownership and permissions so that I don't have go use these terminal commands to remove individual files/folders, but instead just use a file browser?  ~Richard

Yes, you can run nautilus (with root privileges)..

```
gksu nautilus
```

---

### Post by reklabunde on 2007-11-11
Nautilus works great!  Again, thank you!  I could never expect such a helpful community from Microsoft!

---

