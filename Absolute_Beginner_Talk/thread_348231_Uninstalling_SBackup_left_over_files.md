---
title: "Uninstalling SBackup: left over files"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by beaulanger on 2007-01-28
Deleting left over .ful file
and
/var/Backups folder:

I uninstalled SBackup through Synaptic but there is a file called 
/home/beau/2007-01-27_20.36.42.935348.beau-desktop.ful , the path I set for my backup. It is locked and I can't figure out how to delete it. 
Oh, in addition  there is a folder /var/Backups with files in it. I guess that has to be deleted too? If so I'll need to remove that folder too. 
Any help would be appreciated. Please keep it simple as I am a noob. Thanks.

[COLOR="Red"]**EDIT: **[/COLOR] I found this and it worked for the .ful folder but still wondering _what the /var/Backups is for?_ Looks like it has nothing to do with SBackup by reading the text file there. Is this correct? Thanks.

[COLOR="DarkGreen"]**[B]Deleting write protected files and folders:**

Alt-F2
Code:  gksudo nautilus
This will launch a file browser as root. You can then go to the folder and delete it.

.............or use this...................

To get permission:
"sudo rm YOUR_FILE"

To remove a folder containing files:
"sudo rm -R YOUR_FOLDER"

[/B][/COLOR]

---

