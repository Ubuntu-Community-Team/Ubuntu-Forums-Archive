---
title: "[SOLVED] Changing directory ownership"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-11
I created an Encrypted folder with Truecrypt under the FAT file system, and now it seems that I cannot change ownership of the folder. I was reading on another thread that FAT does not allow you to change ownership of the file. when I go to folder properties, it tells me that root is the owner, therefore I cannot change permissions. I entered the su command at terminal, however, it still does not let me access write anything to the folder. I also tried the change ownership command, and it does not allow me to use this folder. What are my options to be able to write to this folder? If it is loggin is as root, how do I do that, where it will apply to the folder itself, not just terminal? thanks for the help

---

### Post by wormser on 2007-12-11
I do not know if this is going to do the trick but it is worth a shot.  The command opens Nautilus file browser with root  privileges.  

```
gksudo nautilus
```

---

### Post by fmbugdadi on 2007-12-11
Yes, that actually did work. It is not exactly what I had in mind, none the less, it worked. Thanks again, for helping close out another thread....

---

