---
title: "[SOLVED] I'm trying to free up hard drive space, but after deleteing 10G, free space"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-13
I just deleted about 10 gigs worth of videos downloaded via Miro, but for some reason, my hard drive's free space count hasn't really budged at all.  I've sometimes found stuff hiding in a .Trash folder, but I've checked the one in my home folder as well as my girlfriends home folder and both are empty.  I've also scanned my entire file system twice using Disk Usage Analyzer, and the folders that were once taking up a lot of space show that they aren't anymore.  What's going on here?

---

### Post by Iandefor on 2008-03-13
Trash folders can sometimes be created in /home. 

Try "ls -ladh /home/.Trash*" The h flag should make the folder sizes human-readable, so it shouldn't be too hard to see if they got moved to one of those directories.

Also, how did you delete the files? Via cli (and if so, what exact command did you use?)? Through Miro?

---

### Post by bhold on 2008-03-13
I've seen this symptom before also, not only on linux but some commercial unix versions as well. I believe some of the disk usage stats are maintained in multiple places (memory resident and disk resident). Try a reboot to get everything back in sync. (Sorry for the MS-like suggestion, hope it helps.) 

If the reboot does not help, then your first approach was probably correct, the files are probably still out there somewhere although I have no idea where if not in trash.

---

### Post by diablo75 on 2008-03-13
> **Iandefor said:**
> Trash folders can sometimes be created in /home. 

Try "ls -ladh /home/.Trash*" The h flag should make the folder sizes human-readable, so it shouldn't be too hard to see if they got moved to one of those directories.

Also, how did you delete the files? Via cli (and if so, what exact command did you use?)? Through Miro?

I've checked, and there is no hidden .Trash folder in /home .

To delete the files I loaded Nautilus as root, and then went into the .miro folder, found the folder containing all the videos, and just deleted them all.  But I didn't notice them going into the trash bin.  Did they go somewhere else?

---

### Post by diablo75 on 2008-03-13
> **bhold said:**
> I've seen this symptom before also, not only on linux but some commercial unix versions as well. I believe some of the disk usage stats are maintained in multiple places (memory resident and disk resident). Try a reboot to get everything back in sync. (Sorry for the MS-like suggestion, hope it helps.) 

If the reboot does not help, then your first approach was probably correct, the files are probably still out there somewhere although I have no idea where if not in trash.

I've also rebooted, and the usage hasn't changed.

I also found another thread that showed how to clear the aptitude cache, but that didn't really free up a lot of space...maybe a gig and half...

:(

---

### Post by diablo75 on 2008-03-13
I found all the junk.  It was located in /root/.Trash/

***SHWING!***

---

### Post by Iandefor on 2008-03-13
For future reference, if you want a context-menu entry to bypass the trash and actually delete a file, you can enable it with the following command:

```
 gconftool --type=bool -s /apps/nautilus/preferences/enable_delete 1
```There's a checkbox for it somewhere in the Nautilus preferences pane, as well, if you want to go looking. I think it's under "Behavior".

---

