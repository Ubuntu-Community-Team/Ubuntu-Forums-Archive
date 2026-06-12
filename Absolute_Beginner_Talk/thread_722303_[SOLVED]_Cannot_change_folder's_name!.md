---
title: "[SOLVED] Cannot change folder's name!"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-12
Hello

I've been having troubles here and there as an Ubuntu Gutsy absolute beginner, but never I'd have imagined I'd find it impossible (all of a sudden) to change a folder's name from "untitled folder" to "whatever"! I tried to create + rename folders on desktop, home, documents, to no avail. No matter what I do, right-click + rename or F2, I can't change the damn folder's name. 

Please help. 
Thanks

---

### Post by jan quark on 2008-03-12
are you getting any error messages
or does the renaming just does not show any effect?

---

### Post by imanoob on 2008-03-12
What are you trying to name it as?

---

### Post by al.adab on 2008-03-12
No, I don't get any error message. The folder's name "untitled folder" (as I create it) remains as it is (blue-highlighted) whatever key I press. The same happens if I click elsewhere, click again on the folder, right-click + rename or press F2. I also to change the name in "properties" to no avail. The "permissions" seem to be as they should:
-Owner XXX - Folder Access: Create and Delete Files - File Access: ---
-Group XXX - Folder Access: Access Files - File Access: ---
- Others: Folder Access: Access Files - File Access: ---

---

### Post by OffAxis on 2008-03-12
Try opening up a terminal and renaming the folder from a command line. At a minimum, it'll error out and print an error message to the terminal, and you can post that.

```

cd /into/the/appropriate/folder
sudo mv "New Folder" "What you really want to name it"
```


you could also forego renaming "New Folder" and create a folder directly with either
```

mkdir "folder name"
```
(which will create the folder with the current user's ownership)
or 

```
sudo mkdir "folder name"
```

(which will create it with root ownership)

---

### Post by al.adab on 2008-03-13
apologies for not following up. I was fed up with this and other bugs and decided to re-install gutsy one more time, mainly hoping it doesn't freeze. Thanks for your help.

---

