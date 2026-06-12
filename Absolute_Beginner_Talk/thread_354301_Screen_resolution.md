---
title: "Screen resolution"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Atanvarno on 2007-02-05
I'm an absolute beginner at Linux, yet I've somehow installed Ubuntu successfully. The only thing is I can't change my screen resolution higher than 1024 x 768 (the other options are 800 x 600 and 640 x 480). I know that my screen works happily at 1280 x 1024, but I can't work out how to change it.

My other problem is there's no sound coming out, but I want to fix the screen res first.

Screen: Samsung SyncMaster 191T
Graphics: nVidia GF 6200 512MB DDR2 TV DV
Motherboard: Asus P4P800-E
CPU: Intel 3.2 GHz

I will happily supply any other information needed; if you know what's wrong, can you give really simple step-by-step instructions?

Thanks.

---

### Post by shareMenaPeace on 2007-02-05
Check out this for the resolution issue
[http://ubuntuforums.org/showthread.php?t=187855&highlight=Samsung+SyncMaster+191T](http://ubuntuforums.org/showthread.php?t=187855&highlight=Samsung+SyncMaster+191T)

---

### Post by Atanvarno on 2007-02-05
Okay, I'm sure that thread is a step in the right direction. I gather I need to manually edit xserver.xorg, and in the "Monitor" section alter HorizSync and VertRefresh to match my monitor. (Changing to 30-65 and 50-75, respectively?)

However, when I type sudo dpkg-reconfigure xserver.xorg into Terminal I get:

Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed
atanvarno@agememnon:~$ 

Oh god.

I realise that I'm probably being a terrible newbie, but this is my first time anything Linux, so more help would be appreciated.

---

### Post by johnc4510 on 2007-02-05
the command is:
sudo dpkg-reconfigure xserver-xorg
copy and paste this in the terminal

---

### Post by Atanvarno on 2007-02-05
You have sloved all my problems. My thanks to both of you.

---

### Post by johnc4510 on 2007-02-05
Our pleasure!!

---

