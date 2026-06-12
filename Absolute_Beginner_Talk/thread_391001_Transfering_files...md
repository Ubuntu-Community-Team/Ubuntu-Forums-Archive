---
title: "Transfering files.."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by steevz on 2007-03-22
Okay, here is my problem.

I want to move a folder, World of Warcraft

from
~/.wine/drive_c/Program\ Files/ 

to
/media/sda1/Program\ Files/

If I try to move it from window to window it tells me I don't have permission.

I tried the command

sudo cp ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/ /media/sda1/Program\ Files/

With no luck. How can I copy the directory from Wine to Windows? Or is it not possible cause the sda1 drive is NTFS.

Any help highly appreciated. Thanks.

---

### Post by ubuntu27 on 2007-03-22
You can[ install this program]("http://www.chrysocome.net/explore2fs") so you can access ext3 filesystem from Windows OS.


[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by steevz on 2007-03-22
Cool.. with that program I was able to export the World of Warcraft folder to Windows without having to go through the long installation of 9 CDs and then updates. One problem I have now though, when I try to login to WoW it loads but then the login and password doesn't show up. It's just the background for the login screen.

---

