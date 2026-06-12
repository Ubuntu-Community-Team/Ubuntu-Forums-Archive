---
title: "Deleting folder via terminal"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-04
how do I do it?

I've got a folder in /mnt that I want to delete. I've tried rm -d folder but that doesn't work.

Also, I've got a folder i want to rename, how do I do that? 

ta :D

---

### Post by daniminas on 2006-12-04
to delete an empty folder:

```
rmdir folder_name
```

to delete an non-empty:

```
rmdir -R folder_name

```

---

### Post by lamego on 2006-12-04
To delete a folder and its entire contents:
```
sudo rm -rf folder
```
**BUT PLEASE BE CAREFULL**

---

### Post by steve.horsley on 2006-12-04
**gksudo nautilus** will give you a GUI file manager with full access rights. This may be more convenient for you than command-line file management.

---

### Post by insub2 on 2006-12-04
> **linuxbun said:**
> how do I do it?

I've got a folder in /mnt that I want to delete. I've tried rm -d folder but that doesn't work.

Also, I've got a folder i want to rename, how do I do that? 

ta :D


to delete a folder:
```
$rmdir /name/of/folder/
```

to rename a folder:
```
$mv /name/of/folder/ /new/name/of/folder/
```

Note: you may have to use "sudo" if you don't have write permission for the folders

Note2:I didn't know how to rename offhand so I did a google search for "terminal rename directory" to get the answer.  google is your friend.

---

### Post by useResa on 2006-12-04
You could also use the *rm* command.  To remove directories and their contents recursively use ```
rm -r 
```  If you would like to remove without getting prompted at all, use ```
rm -rf 
```  If you would like to see all possible options for the *rm* command, you can type ```
rm --help
```

---

### Post by useResa on 2006-12-04
You could also use the *rm* command.  To remove directories and their contents recursively use ```
rm -r directory_name
```  If you would like to remove without getting prompted at all, use ```
rm -rf directory_name
```  If you would like to see all possible options for the *rm* command, you can type ```
rm --help
```

---

### Post by linuxbun on 2006-12-04
Brilliant! Thanks all!! :D

---

