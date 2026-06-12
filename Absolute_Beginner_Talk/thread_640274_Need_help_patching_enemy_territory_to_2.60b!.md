---
title: "Need help patching enemy territory to 2.60b!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by benjamin222 on 2007-12-14
Heya, I just installed enemy territory 2.60, trying to patch it to 2.60b. Downloaded the patch, all it had in it for linux was 2 files, etded.x86, and et.x86. Naturally I'm assuming to just copy and paste those files to the ones in my game folder, So I'm trying that but its a no-go. For some reason the folder is protected and it wont let me un-protect it. Also good to mention when I try to play enemy territory right now as 2.60, it gives me an error message "cant write to hunkusage.dat" and wont let me save any profiles. Yeah, guessing again because the folder is protected. 

Soooo how do I un-protect the folder? When I click on its properties everything is grayed out. The closest I can do to unprotecting is taking my ubuntu partition, right clicking, going to properties, changing everything to "can view and modify content" and applying that to all subfolders, except when I do that it stalls at 0% and is unable to do it.

Sorry about my disorganization.. so I guess my real question is why am I not showing as the primary user and why cant i change my folder permissions. If anyone knows what I can do to get enemy territory working I shall give you BIG HUGS! .. except they will be virtual hugs so we'll have to hug our monitors at the same time.

Thanks!

---

### Post by jordanmthomas on 2007-12-14
While I'm not exactly sure what's causing your problem, I always use the installer from here and I've never had an issue getting into games.

[http://y.mrbass.org/et/et-linux-2.60.x86.run.zip](http://y.mrbass.org/et/et-linux-2.60.x86.run.zip)
(rename to et*.run and chmod +x it, then sudo ./et*run)

Also, try fixing the permissions on your .etwolf folder.
```
sudo chown -R $USER:users ~/.etwolf
```

---

