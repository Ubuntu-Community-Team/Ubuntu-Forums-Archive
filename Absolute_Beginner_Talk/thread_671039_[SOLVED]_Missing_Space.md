---
title: "[SOLVED] Missing Space"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by talsemgeest on 2008-01-18
Ok, when I select everything in my / folder and click properties, it says that I have 23.8 GB of data, which sounds about right to me. However, when I right click "Filesystem" and click properties, it says I'm using 84.6 GB. Same thing with disk usage analyser.

Where is all of my free space going? Ive made a backup partition which means that I'm just about out of space, so I need to find out what the problem is or I am going to have to format and reinstall.

Thanks in advance...

---

### Post by jeffus_il on 2008-01-18
As a guess, look into Nautilus trash, and .Trash hidden folders. Empty them and see if it makes a change.

---

### Post by renzokuken on 2008-01-18
have you emptied the trash can recently. also, in the root of that drive/folder, check for a hidden folder called **.Trash_*username***, if it's there empty it, sometimes this trash folder doesnt get emptied when you use the trash icon on the desktop

---

### Post by talsemgeest on 2008-01-18
All trash is empty. Same disk usage. Any more ideas? And thanks for the speedy replies

---

### Post by seanmiller on 2008-01-18
From a terminal type...

$ cd /
$ sudo du -sk *

This will list where space is being used by top level directory... you can then work down the tree until you find your rogue 60GB.

eg.

$ cd /home
$ sudo du -sk *

File sizes are in kilobytes so 1GB would be 1024000 etc.

Sean

---

### Post by talsemgeest on 2008-01-18
The missing space seems to be in /root but when I do:

$ cd /root
$ sudo du -sk *

I only get :

4       Desktop
404     nautilus-debug-log.txt

So what do I do now?

---

### Post by talsemgeest on 2008-01-18
Maybe I will try It out from a live cd...

---

### Post by jeffus_il on 2008-01-18
Check the root .Trash***** subdirectory. (under /root)

---

### Post by talsemgeest on 2008-01-18
And there it all is. Previous backups that I deleted while using a gksudo nautilus. Thank you so much for all of your help. Its so good to suddenly have 90 gigs free space. Thanks again!!!

---

