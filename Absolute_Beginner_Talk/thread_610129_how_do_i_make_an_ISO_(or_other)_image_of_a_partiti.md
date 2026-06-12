---
title: "how do i make an ISO (or other) image of a partition for future disk restoring?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-11-11
hey all.

i'm setting up a computer illiterate friend's machine for her, and she unfortunately wants windows. so i've made a small ubuntu partition to use as a restoration tool. what i'm needing help with is finding the best way to burn an image of the primary NTFS partition - either .iso, or whatever recommended format - so that this image can later be used to restore the windows.

i imagine the process would be along the lines of: generate image of ntfs partition. then, when needed, command line erase the ntfs partition, and command line load the saved disk image back into the now-empty ntfs partition. 

i'm just not sure which programs to use for any of these three steps.

thanks!

---

### Post by carloslosgrande on 2007-11-11
[FONT="Comic Sans MS"]Partition Image will do that. In windows I believe something called ghost is used. You can get SystemRescueCD which has PartImage included.
Look here for instructions [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)[/FONT]

---

### Post by newlinux on 2007-11-11
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

ddrescue:

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by sailor2001 on 2007-11-11
> **ijason said:**
> hey all.

i'm setting up a computer illiterate friend's machine for her, and she unfortunately wants windows. so i've made a small ubuntu partition to use as a restoration tool. what i'm needing help with is finding the best way to burn an image of the primary NTFS partition - either .iso, or whatever recommended format - so that this image can later be used to restore the windows.

i imagine the process would be along the lines of: generate image of ntfs partition. then, when needed, command line erase the ntfs partition, and command line load the saved disk image back into the now-empty ntfs partition. 

i'm just not sure which programs to use for any of these three steps.

thanks!

from xp to vista, there is already a restore point in your programs. Visit it often to install newer restore point

---

### Post by ijason on 2007-11-11
**@ newlinux** : DDrescue looks like it will do the trick. do you know if there is a way to compress the image any? speed isn't too much of a problem because if used it will be a rescue, so it can take as long as it needs.

i'm also wanting to basically make an .img, and leave it on the ubuntu partition. then when it's needed have a big fat icon to click that will run the script to wipe the ntfs partition and reload all the files out of the saved .img onto that partition.

---

### Post by newlinux on 2007-11-12
I have not used compression with ddrescue, so I can't say for sure, sorry.

---

