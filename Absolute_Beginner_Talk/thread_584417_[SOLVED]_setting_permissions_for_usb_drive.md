---
title: "[SOLVED] setting permissions for usb drive"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by faust99 on 2007-10-21
Sorry to be such a noob, but I can't work out how to set all of the permissions on my external usb hard drive (ext3) to me, rather than root. 

I backed up my home file there and then installed 7.10, and now want to copy the files back to my home folder from the external drive. I am able to set permissions one folder at a time when I log in to nautilus as root, but there are so many folders and files there that I would like to do it all in one hit if possible?? 

Any advice and help would be highly appreciated. I've working on this all day but am stuck...:confused:

---

### Post by p_quarles on 2007-10-21
Do you know the mount point of the drive? Once you do, this will be easy.

In Nautilus, it should indicate something like "media/external-hd" as the mount point. If you can't find it this way, open a terminal and type:
```
ls /media
```The output will most likely point you in the right direction. If you're not sure, post it here.

After you get this info, go to the terminal and type this (edited following faust99's correction below):
```
sudo chown -R *username* /media/*external-hd*
```Replace *username *with (yes) your username, and *external-hd* with the drive's actual name. And you're set.

---

### Post by faust99 on 2007-10-21
Thank you so much for that. Such an easy operation in the end. 

I should add, if anyone has this problem in the future that I had to (obviously) preface the terminal command with 'sudo', and the 'r' had to be a capital 'R' i.e.

sudo chown -R *username* /media/disk

Thanks again p_quarles!

---

### Post by p_quarles on 2007-10-21
Yeah, you're right, that should be a capital 'R'. Many commands take the -R option to make the operation recursive through subdirectories, and some take either case. I forgot that chown wasn't one of them.](*,)

By the way, you can increase the chances that other users will see this by going to the top of the thread, clicking on "Thread tools", and then choosing "mark as solved."  That will help people when they run searches.

Glad I could help.

---

### Post by gewitty on 2008-03-25
Small point - but it also requires a re-boot for the changes to take effect (at least, it did on my machine).

---

### Post by drs305 on 2008-03-25
> **gewitty said:**
> Small point - but it also requires a re-boot for the changes to take effect (at least, it did on my machine).
Usually you don't have to reboot but you may have to refresh/reload your file manager to actually see the changes.

---

