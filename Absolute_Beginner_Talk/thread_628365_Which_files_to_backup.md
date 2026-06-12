---
title: "Which files to backup"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by aridus on 2007-12-01
In 7.10 I have set up a backup system for my essential files to an external USB drive, backing up my documents, pictures and music, using sbackup. It seems to work well. I would also like to backup other essential files. For me these are evolution e-mail and  account settings, tomboy notes, and spelling dictionaries in OpenOffice that I have added words to (bookmarks are taken care of by FoxMarks). I am not concerned with backing up other settings as I don't feel the need for a complete mirror; I just want all essential items backed up so that if my computer explodes I can reinstall 7.10 somewhere else and do a recover from my USB drive. Could somebody please kindly indicate where my evolution e-mail and settings, tomboy notes, and spelling dictionaries are (my understanding of the file system in Ubuntu is very limited!) so that I can add them as backup directories to sbackup. (Obviously with respect to evolution there is a backup system in 7.10 but I would like everything to happen automatically, and I can't see how I can access the tar command that evolution must be using so that I can locate the directories). 

Subsidary questions: what are the commands and paths to set in System > Preferences > Sessions > Startup Programs so that I could have evolution and tomboy start automatically at book?

With thanks!

---

### Post by nhandler on 2007-12-01
I don't know about where the files are located, but getting the programs to start automatically is easy. For evolution, simply put 'evolution' (without the 's) in the command box. For tomboy, put 'tomboy'. Then set any name and comment.

---

### Post by monte48lowes on 2007-12-01
I prefer to backup my entire /home directory. Doing this backs up all of my configuration files as well as email, bookmarks, wallpapers etc.

Mike

---

### Post by aridus on 2007-12-01
Thanks for the evolution and tomboy commands, which work fine.

If I backup the entire home directory isn't there a lot of unnecessary stuff being added (such as installed programs)?

---

### Post by meindian523 on 2007-12-01
Usually,user settings for "application" are found in /home/username/.name_of_application

To see these folders(the .name_of_application ones),pres Ctrl+H or View>>Hidden files

---

### Post by aridus on 2007-12-01
Hmmm. OK perhaps if I backup my whole home drive that will do what I need. But within the home drive are there any folder / file types that I should not backup?

---

### Post by meindian523 on 2007-12-01
Umm.you can backup your whole /home but you will have to give a specific option,please check ```
man cp
``` or ```
man tar
``` to get those hidden files/folders copied/tarred too......

AFAIK,there's nothing in the /home which should not be backed up,but this is just a guess,maybe wait for someone with more experience?

---

### Post by monte48lowes on 2007-12-01
Addtionally check into 'rsync'. It performs like cp, however it will only copy the files that have changed.

Mike

---

### Post by aridus on 2007-12-01
My interest is only in a non-command line program (or at least in a program that has a front end). I can't really manage rsync and the like. The beauty of sbackup is that it sets the scheduling for you. 

BTW there is another thread going about which is the best backup program to use ([http://ubuntuforums.org/showthread.php?t=628242](http://ubuntuforums.org/showthread.php?t=628242)).

M

---

