---
title: "Need Help Please"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by averagebeatboy on 2007-12-21
I used Time Vault to backup my files on Fri. 21, Dec..  What I did was backup from My Ubuntu "Gutsy Gibbon to an external harddrive.  All seemed to go very well.  Now in my external harddrive I have the following files: Catalog, Flyback, Internal, and Pending.  Whenever I shut down my external harddrive it asks if I want to empty the trash when I tell it to empty the trash it is unable to do so saying I do not have the proper permissions.

I would love to get this off of my external drive and try the new edition of Flyback or Time Machine.  I am not sure what name they have choosen for the application.  I downloaded the latest version, but it still will not take the oler versions of the backup I made from my external drive.

Any help would be so greatly appreciated. In my Trash: folder on Ubuntu I have the same 4 folders and when I try to delete them I get the following mesage: ERROR WHILE DELETING "HOME/BAEK...H/CATALOG CANNOT BE DELETED BECAUSE YOU DO NOT HAVE PERMISSIONS TO MODIFY ITS PARENT FOLDER.

ANY HELP WOULD BE SO GREATLY APPRECIATED.

AVERAGEBEATBOY

---

### Post by spiderbatdad on 2007-12-21
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by thelatinist on 2007-12-21
```
cd ~/.Trash
sudo rm -rf Catalog Flyback Internal Pending
cd [external harddrive]
sudo rm -rf Catalog Flyback Internal Pending
```

You will need to know the path to the folder on your external hard drive which contains the folders you want to delete.  Replace [external harddrive] in the third command above with this path.  For instance, if your external drive is mounted at /media/external, and those folders are in that drive's root, you would use cd /media/external.

Be very careful!  sudo rm -rf is the command people warn you about because it will delete anything, no questions asked.  If you are not in the correct folder when you issue this command, it may delete files you want or need.  You have been warned.

---

### Post by averagebeatboy on 2007-12-23
Thank you.  In my frustration I reinstalled Ubuntu and this time will rebuild it again.  Bu I have written down what has been given to me and will use them if this happens to me again.

Thank you both and have a Happy Holiday Season.

Sincerely,

Averagebeatboy  :)

---

