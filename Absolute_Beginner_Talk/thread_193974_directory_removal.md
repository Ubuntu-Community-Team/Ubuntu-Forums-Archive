---
title: "directory removal"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by wana10 on 2006-06-10
when i try to delete a folder i'm told
error while moving
Cannot move "/home/wes...-20060501" to the trash because you do not have permissions to change it or its parent folder.

so i go into terminal and try
```
wesley@ubuntu:~$ sudo rmdir ~/all-20060501
Password:
rmdir: /home/wesley/all-20060501: Directory not empty

```

so how can i clear the folder without having to manually delete all 129 files in the folder?
thank you for your help

---

### Post by zugu on 2006-06-10
Wel, obviously, the rmdir command is used to remove directories, NOT files. The command used to delete files is ```
rm
```, however, it is a dangerous command to use, because improperly used can cause catastrophes. Once you've "rm-ed" something, there's no way of bringing it back.

I have never properly learnt the command line switches for this command, so I won't tell you how to remove the whole directory and the files in it at once, because I might be wrong, but you can use```
rm /home/wesley/all-20060501/*
```assuming the files you want to delete are in the /home/wesley/all-20060501/ directory, and then you can just ```
rmdir /home/wesley/all-20060501/
```. Now you've removed the files in the directory and the directory itself. That's it.

---

### Post by 5-HT on 2006-06-10
rmdir only works on empty directories. You can either delete all the files in the directory first (e.g., sudo rm /home/wesley/all-20060501/*) and then remove the directory using rmdir, or just remove the directory and all the files contained within by doing
```
 sudo rm -rf /home/wesley/all-20060501/ 
``` 
Be careful though as that previous command will not prompt you for each file to delete (so make sure you are deleting the wanted directory)! 
The -r flag in there is for recursive removal, and the -f is for force (no confirmation).

If you want to be prompted to confirm the removal of every file
```
sudo rm -ri /home/wesley/all-20060501/ 
``` 
The -i is for interactive (requires confirmation).

As an aside, you should have read/write permissions for everything in your home directory. You can always change permissions of files/directories using chmod. For a guide to chmod, refer to the manual page
```
 man chmod 
``` 
Hope that helps.

EDIT: too slow

---

### Post by zugu on 2006-06-10
Actually, 5-HT was the man with the flags ... :)

---

### Post by wana10 on 2006-06-10
worked perfectly thank you for your help

---

