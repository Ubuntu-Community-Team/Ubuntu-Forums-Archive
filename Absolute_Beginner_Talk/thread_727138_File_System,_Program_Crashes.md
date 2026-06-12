---
title: "File System, Program Crashes"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Captaingracekidd on 2008-03-17
[http://ubuntuforums.org/showthread.php?t=721477&highlight=AWN+beryl](http://ubuntuforums.org/showthread.php?t=721477&highlight=AWN+beryl)

Since I made this post I have come to the conclusion that the problem is greater than I thought. I can se my home folder but trying to access any other subfolder biunces me back to the homefolder. In Firefoz I cannot save bookmarks or download a file without the program crashing.

Can this be due to me installing AWN and Beryl, or maybee some of the dependencies? 

I have tried shutting of AWN and Beryl but the problem is still present.

I need to get to the info in my sub-folders asap, please help me!

Regards// F

Ps. I would rather not upgrade to Gutsy (having hade bad experiences with this distro).

---

### Post by handydan918 on 2008-03-17
> **Captaingracekidd said:**
> [http://ubuntuforums.org/showthread.php?t=721477&highlight=AWN+beryl](http://ubuntuforums.org/showthread.php?t=721477&highlight=AWN+beryl)

Since I made this post I have come to the conclusion that the problem is greater than I thought. I can se my home folder but trying to access any other subfolder biunces me back to the homefolder. In Firefoz I cannot save bookmarks or download a file without the program crashing.

Can this be due to me installing AWN and Beryl, or maybee some of the dependencies? 

I have tried shutting of AWN and Beryl but the problem is still present.

I need to get to the info in my sub-folders asap, please help me!

Regards// F

Ps. I would rather not upgrade to Gutsy (having hade bad experiences with this distro).
Could be a full partition...post the output of ```
df -h
```

---

### Post by Captaingracekidd on 2008-03-17
Here you go...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  4.3G  4.5G  50% /
varrun                125M  108K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb            125M  112K  125M   1% /proc/bus/usb
udev                  125M  112K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   33M   92M  27% /lib/modules/2.6.20-15-generic/volatile
/dev/sda5             9.2G  166M  8.6G   2% /boot
/dev/sda3             8.3G  7.2G  706M  92% /media/sda3
/dev/scd0             185M  185M     0 100% /media/cdrom0

thanks for helping :)

---

### Post by handydan918 on 2008-03-17
> **Captaingracekidd said:**
> Here you go...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  4.3G  4.5G  50% /
varrun                125M  108K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb            125M  112K  125M   1% /proc/bus/usb
udev                  125M  112K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   33M   92M  27% /lib/modules/2.6.20-15-generic/volatile
/dev/sda5             9.2G  166M  8.6G   2% /boot
/dev/sda3             8.3G  7.2G  706M  92% /media/sda3
/dev/scd0             185M  185M     0 100% /media/cdrom0

thanks for helping :)

Interesting partitioning scheme.
Now, grub has gotten a little bigger over the last couple of years, but I really think 9.2GB is a little excessive. 250MB ought to be plenty, if you really even want a /boot partition. 
I would consider both of these things:
1) Clean up /dev/sda3 (media) and delete as much as you can. Dump duplicates, old files, etc.
once you've done that, and you can get into your files again, back it all up (dvd/cdrom?) and reinstall, but try a more useful partition scheme.
Say, 
root=10-12GB
/home=remainder
Impossible to advise on how to best back up without more detail. If you are networked to another box with lots of room, i would consider copying files over via scp or something else that can be done easily from a terminal...

---

### Post by Captaingracekidd on 2008-03-18
Okej, it will be difficult to clean up the folders when I cant see the content. Everything is mixed, old and new. 
So there is absolutely no way to fix this... the reinstallation of all my apps etc will take me three days so Im not so kean on reinstalling. :/
Is there no other solution?
Thanks a bunch for the help. F

---

### Post by handydan918 on 2008-03-18
Sorry for the delay...
Can you see the files from a console? (Safe mode or ctrl+alt+F1)?
If so, you can delete unnecessary files from there. This will require use of the dreaded "rm" command, so verify everything anyone (including me!) tells you. There is no recovery (practically speaking) from a bad "rm".

---

