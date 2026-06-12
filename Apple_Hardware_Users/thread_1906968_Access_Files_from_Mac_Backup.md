---
title: "Access Files from Mac Backup"
date: 2012-01-10
forum: Apple Hardware Users
---

### Post by WarrenBowling300 on 2012-01-10
So after performing these three commands  as sudo I successfully transferred all files onto a new hard drive.:grin: (Look at this thread for some more info: [http://ubuntuforums.org/showthread.php?t=852144](http://ubuntuforums.org/showthread.php?t=852144)) Thanks to all the members that posted to that forum for their help.

1. sudo cp -R /path/to/macdrives /Seagate/WarrenBowling300/newdirectory 
2. cd ~/Seagate/WarrenBowling300 
3. sudo chown WarrenBowling300.WarrenBowling300 *

I did not want to run sudo nautilus and risk destructing the documents I need.:sad:  But now that I have a copy of the whole hard drive I can mess with it  and try whatever. I did run sudo chown WarrenBowling300.WarrenBowling300  * but everything it showing up as a blank text file. :confused:What do I do?

The directory to the file is (if it helps): Seagate/WarrenBowling300/Back-up/Backups.backupdb/(then various dates I backed up)

Thanks for the help

---

