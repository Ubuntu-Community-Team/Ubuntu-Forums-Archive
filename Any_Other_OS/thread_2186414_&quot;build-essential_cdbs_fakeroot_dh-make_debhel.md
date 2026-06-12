---
title: "&quot;build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6&quot; removal!"
date: 2013-11-07
forum: Any Other OS
---

### Post by limGE13 on 2013-11-07
Hello everyone! extremely new here and in ubuntu too.. i needed to check if i could improve my sapphire 2600 pro performance on my desktop. i have linux mint 15. following this [http://community.linuxmint.com/tutorial/view/1316](http://community.linuxmint.com/tutorial/view/1316) (also found in this forum [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)) i tried it but no luck. so i cleverly thought that i should mess around a bit.   The first instruction was: sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6  after trying to make it work without luck, i thought i should: sudo apt-get remove build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6   my terminal asked to write Yes, do as i say! and.... the entire mint was gone. everything... it just restarted doing memtest...  i found a similar question in this forum from someone asking if its good to remove those packages ([http://ubuntuforums.org/showthread.php?t=1996685](http://ubuntuforums.org/showthread.php?t=1996685)) and the responses were not DONT DO IT! so i did it!  any ideas for data recovery???? i am ready to format but there is some current work not backed up! any ideas in general?????  thanks a lot and excuse any rookieness of mine!

---

### Post by Impavidus on 2013-11-07
Running **sudo apt-get remove the-wrong-package** can hose your system, but cannot destroy your user files. With the system unbootable you can access them using a live disk, the same one you can use for reinstalling.

---

### Post by limGE13 on 2013-11-07
thanks for replying! i thought the same you do! but after watching everything getting uninstalled i know what happened! the thing is that i cant even access data in hard disk through the live cd! i sign in to the drive but no file is there!

---

### Post by oldos2er on 2013-11-07
Moved to Other OS/Distro Support.

---

