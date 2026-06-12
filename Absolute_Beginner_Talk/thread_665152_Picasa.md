---
title: "Picasa"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by tjefferson on 2008-01-11
Hello,

I'm a recent convert from Windows, where I was very comfortable with Picasa as my photo manager. However, when I installed it for Ubuntu using the download online, I screwed up by allowing it to scan my entire disk for images, with over 9000 pictures as a result. The program crashed twice with a window that read "Fatal Error," so I removed it using synaptic. I installed it once more, but it displayed every photo again. I quickly removed it. I am concerned that all of its files might not be completely gone, which would affect future attempts at re-installation.

Secondly, is there a more stable photo manager for Ubuntu? I don't care much for F-Spot. I'd love to use Picasa, but I can't. Thanks much.

---

### Post by exile on 2008-01-11
Uninstalling picasa won't necessarily remove your config/photo database files.

Try uninstalling picasa, then looking in your home directory (showing hidden files CTRL-H) and look for a .picasa directory or something like that and renaming it (delete it after your sure it's worked as expected). Install Picasa again. It shouldn't be necessary to uninstall picasa, you just need to remove the photo db.

Now, I've never actually used picasa, so it might not produce a directory called .picasa, I've only ever used f-spot but the theory is the same.

Good luck

---

### Post by finer recliner on 2008-01-11
when you uninstall an application in linux, the application (usually) does not remove the user's personal settings.

user's personal settings are located in your home folder (~). they are usually hidden. (hidden files/folders always start with a period (.)) 

i have not personally used picasaa, but its personal settings are probably located in a file or folder called .picasa or .google-picasa or something similar.

uninstall picasa using the package manager as have been trying, then remove the personal settings file/folder. then try to reinstall.

---

### Post by nikoPSK on 2008-01-11
It won't remove your settings unless you purge it. :KS

---

