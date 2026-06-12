---
title: "Can't Chown certain Folders"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by rolfotto on 2006-04-26
Okay,

I posted a problem in the DD forum:
[http://ubuntuforums.org/showthread.php?t=166061](http://ubuntuforums.org/showthread.php?t=166061)

But in the meantime, I found out it probably just permissions.  I have some folders that are owned by root, but I want them under my user name (rolf).  I wrote in the terminal:

> $ pwd
/media/hdb1
$ ls
[COLOR="Blue"]ebay  lost+found  Pictures  Rolf[/COLOR]
$sudo chown -R rolf Pictures
$sudo chown -R rolf ebay
$sudo chown -R rolf Rolf

Only the folder Pictures took "rolf" as owner.  The folder Rolf and ebay still have root as the owner.  I created these folders earlier, so it shouldn't be system owned by design (moving them around in Mepis made them so).  All the subfolders of all the folders are now owned by "rolf", which is good.  I just don't understand why the parent folders refuse to cooperate.

---

### Post by auroraborealis on 2006-04-26
1. cat /etc/passwd|grep <your username>
2. Find your user/group number (probably 1000)
3. in /etc/fstab under options, have uid=<that numer>,gid=<same number>,<other mount options>

---

