---
title: "Mounted Volumes on Desktop"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by modernsapien on 2008-03-05
New to Linux and I completely love it :). I'm dual booting right now because my wife doesn't want me to get rid of windows *sigh*. I have two NTFS partitions, one is the windows os, and one is recovery ( To reinstall windows. ) I would like to keep the Windows OS volume mounted but not on my desktop. I know there is a way but I can't find it. Thanks in advance.

---

### Post by spiderbatdad on 2008-03-05
see how it's done here:[http://ubuntuforums.org/showthread.php?t=432659](http://ubuntuforums.org/showthread.php?t=432659)

the only part missing is the first part...make a directory in which to mount the volume:```
sudo mkdir /media/sdc1
```for example

Also checkout ntfs-config to help you.

---

### Post by tarehart on 2008-03-05
Having an icon for your Windows OS on the desktop does not necessarily mean it's mounted there. I'm guessing it's actually mounted in /media/

---

