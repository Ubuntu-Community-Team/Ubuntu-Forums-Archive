---
title: "help changing UID (my account disappeared)"
date: 2011-01-12
forum: Apple Hardware Users
---

### Post by stoopkitty on 2011-01-12
so, i did something not very smart...

i was trying to fix the permissions issues between mac os and ubuntu from ubuntu so i could view my mac files (i'm dual booting (using refit to fix all of the partition/hfs+ issue things which works great) and my uid in mac is 501), so i googled it and found [this article]("http://ubuntuforums.org/showthread.php?t=109752") and sudo gedit /etc/group and /etc/passwd and changed my uid from 1000 to 501 in both files, everywhere i saw the number 1000. so, then i ran some other sudo command in terminal (don't even remember what it was but it doesnt matter because) it wouldnt let me because it was like "couldn't find uid 1000" or something like that. i figured i needed to restart x so i logged out and was going to log back in and there were no accounts there just the "other" thing.

so, is there a way to get my account back? it seems the best way to go about this would be to change back my uid in those file (/etc/group and /etc/passwd), but there is no way (that i know of) for me to access my filesystem. my mac os doesn't even recognize (it wont mount, but ive given up) my ubuntu filesystem. i have no way to login i don't think. i know everyone hates it when people log in as root, but if i could somehow do that, i promise i would only fix my problem without tampering with anything else :) or not if there is a better way to do it. i have a live cd(10.04) but i'm not sure if you can read/write and do everything i would need to and if it would also work with my dual boot refit setup being able to find/read my ubuntu system.

sorry for the long post... any suggestions?

btw, this isnt urgent, i dont really have that much data on my ubuntu account that i cant go without, a lot of it is online and on mac os partition also

---

### Post by stoopkitty on 2011-01-14
bump?

---

### Post by hawkmage on 2011-01-14
It sounds like your Ubuntu home directory and its files are still owned by UID 1000.  Before going onto the next steps verify that the UID for your account is 501 in /etc/passwd.  

Just to be safe make sure that your HFS+ partitions are not mounted.  Log in as root and run this command:
```
find /home -mount -user 1000 -exec chown 501 '{}' \;
```

This will look for all files under /home that are owned by UID 1000 and change them to be owned by UID 501.

---

