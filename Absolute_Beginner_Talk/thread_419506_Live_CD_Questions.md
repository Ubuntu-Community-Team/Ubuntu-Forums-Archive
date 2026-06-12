---
title: "Live CD Questions"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by techfan92 on 2007-04-23
Hello,

   If I'm running Ubuntu 6.10 from the Live Cd, is there a way I can access my Windows files? Also, when I'm running the Live CD, do I have to worry about running a firewall or an antivirus program?

Thanks.

---

### Post by devnulljp on 2007-04-23
Depends on the format of your windows partition...if its fat32/vfat then it's easy, if it's ntfs it can still be done but you need to load the ntfs modules.

There's a nice howto here: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

If it's vfat though, all you need is 
sudo mkdir /media/windows; sudo mount -t vfat -o rw /dev/hda1 /media/windows

---

