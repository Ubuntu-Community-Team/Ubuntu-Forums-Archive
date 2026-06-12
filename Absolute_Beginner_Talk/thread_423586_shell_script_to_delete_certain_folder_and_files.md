---
title: "shell script to delete certain folder and files"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by hyapadi on 2007-04-26
I'm going to use PHPBBFM  and wonder if I could make some shell script to ease my task on upgrading.

[http://phpbbfm.net/support/docs/install_update_fm.html](http://phpbbfm.net/support/docs/install_update_fm.html)

As can be read there, each time I do upgrade, I must delete certain files and folder. It is troublesome to do it.

After that I must chmod certain files 

[http://phpbbfm.net/support/docs/install_post.html](http://phpbbfm.net/support/docs/install_post.html)

Can somebody help me create a simple script for doing the deletion safely? and another script todo the chmoding?

Thanks :KS

---

### Post by devnulljp on 2007-04-26
A simple way to do it is just to dump the commands you would use into a text file (so, do it once, then copy history to a text file) and set the execute bit (chmod +x)

Something like this:

#!/bin/bash
rm -rf /some/file/to/delete;
rm -rf /some/folder/to/delete;
chmod <code> /some/file/to/chmod;

That will do it. Of course you can get more complex by chekcingfor the existence of the directories/files to delete/chmod first and only going ahead if the conditions is met:

if condition
then
	statement1
	statement2
	..........
else
	statement3
fi

Or a few lines of perl might do too, depends on what you want to do and how simple/complex you want to go

---

### Post by hyapadi on 2007-04-26
For the chmod I think there would be not much problem.

The problem is the deletion.

"Next, delete ALL the existing Fully Modded phpBB files from your forum root directory, EXCEPT for the following directories listed below, do not leave any other directories or files on the server otherwise you may encounter errors later.

    * Keep the cache/ directory (DO NOT overwrite files in this directory with newer ones)
    * Keep the images/avatars/ directory
    * Keep the images/links/ directory   (Only if you have added custom link images)
    * Keep the images/shop/ directory   (Only if you have added custom shop item images)
    * Keep the images/smiles/ directory   (Only if you have added custom smilie images)
    * Keep the mods/games/ directory   (Only if you have added custom games)
    * Keep the mods/toplist/images/ directory   (Only if you have added custom toplist images)
    * Keep the modules/ directory
    * Keep the templates/subSilver/images/icons/ directory   (Only if you have added custom icon images)
    * Keep the templates/subSilver/images/ranks/ directory   (Only if you have added custom rank images)
    * Keep the templates/subSilver/images/themes/ directory
    * Keep the uploads/ directory

We must keep  these folders while delete the rest. How to do it?

I would prefer to have a simple script so I can understand and modified it.

---

### Post by devnulljp on 2007-04-29
You could always just use find and -exec
First figure out a find command that will return only those files you want to delete. You can do it with modification timestamps

find . -type f -ctime 1 -exec rm -rf {} \;

Will delete all files in the current directory and below that was last modified within the last day (1 * 24 hr)

Something like that?
do man find to fiure out te optons you need to id your files.

---

### Post by bashologist on 2007-04-29
> **hyapadi said:**
> I'm going to use PHPBBFM  and wonder if I could make some shell script to ease my task on upgrading.

[http://phpbbfm.net/support/docs/install_update_fm.html](http://phpbbfm.net/support/docs/install_update_fm.html)

As can be read there, each time I do upgrade, I must delete certain files and folder. It is troublesome to do it.

After that I must chmod certain files 

[http://phpbbfm.net/support/docs/install_post.html](http://phpbbfm.net/support/docs/install_post.html)

Can somebody help me create a simple script for doing the deletion safely? and another script todo the chmoding?

Thanks :KS

If you want to chmod those files how they're displayed in there then this should work.
```
[ -d "modules" ] && sudo chmod 0666 images/smiles/ language/*/lang_bbcode.php language/*/lang_faq.php language/*/lang_faq_moderator.php cache/page_perms.php cache/reflog.txt cache/semaphore.ref
[ -d "modules" ] && sudo chmod 0777 modules/ modules/pakfiles/ uploads/ uploads/album/ uploads/album/thumbs/ uploads/attachments/ uploads/attachments/thumbs/ uploads/backups/ uploads/pafiledb/ uploads/pafiledb/screenshots/ uploads/user_avatars/ uploads/user_avatars/tmp/ uploads/user_photos/ cache/backup/ cache/tpls/ admin/backup/ cache/
```

---

