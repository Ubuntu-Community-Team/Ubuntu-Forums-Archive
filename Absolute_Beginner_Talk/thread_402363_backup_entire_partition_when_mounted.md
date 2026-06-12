---
title: "backup entire partition when mounted"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-04-05
I was wondering if there is a way to backup my entire partition while using it? I know I can do it by booting with a live cd and using partimage but thats a little more time consuming than I like. Is this even possible? Thanks

---

### Post by LaurelLynn on 2007-04-05
Dear mikawber,

I´m sure you can do it, the only problem is that partimage won´t be able to read some of the operating systems locked files, if it is the root partition. Also files that change during the backup may retain the old versions.

If this were another operating system I could name, I would say with certainty the backup would be unstable. With Ubuntu the backup would probably be bootable and workable, but I wouldn´t trust it for stability.

It is always best to backup a partition when it is not in use. As an emergency meassure though it might save your bacon. Years of experience teaches me to be careful with backups, one error can make them completely usless.

Laurel Lynn

---

### Post by dannyboy79 on 2007-04-05
i don't know of a tool to backup at the partition level but I use sbackup (also known as simple backup) which can backup everything even from a running system! I have even tested the backup (which is a .tgz archive), HA actually I am using my backup system right now. I restored it to make sure I had a backup that was successful and I knew worked! here is the guide ([http://ubuntuforums.org/showthread.php?t=401425](http://ubuntuforums.org/showthread.php?t=401425)) that I wrote up for testing your backup but if you just want to use sbackup, it's a gui so it's self explainatory. but, there are directories you need to exclude from the archive because they aren't real data locations. (proc, sys and others)  it's all in my guide what you should backup and shouldn't. good luck. oh, partimage is awesome also!!

---

