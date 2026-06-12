---
title: "USB Flash problem"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by nmafzal on 2006-09-19
Hi,
   I have a peculiar problem, when I plug in my USB flash disk it is automatically detected, the icon also appears on the screen, also a window showing its contents appears. But the free space that it shows is not the same, I mean in Win XP it shows 60 MB out of 128 MB free, but here in Linux Ubuntu it shows a mere 6 MB. What could be wrong? Is it making a backup of files and not showing them, I have tried looking at the permissions using ls -s but all is clear there. I need to copy a few files and its turning out to be nightmarish, please anybody help, many thanks,
Best,
Nomi

---

### Post by oedipuss on 2006-09-19
Usually there is a '.Trash' folder where your deleted files go (if you delete them from nautilus; rm from the terminal just deletes them, no questions asked). This is somewhat of a bug when it comes to usb disks, and I think is about to be removed, if it hasn't already. 
Perhaps the reason you're seeing less disk space is because you deleted some files and now they're in the .Trash folder ( the dot is part of the filename, as is the capital 'T'). Try deleting them from a terminal.
If that's not it, then I'm afraid I don't know :(

---

### Post by Obor on 2006-09-19
> **oedipuss said:**
> Perhaps the reason you're seeing less disk space is because you deleted some files and now they're in the .Trash folder ( the dot is part of the filename, as is the capital 'T'). Try deleting them from a terminal.
If that's not it, then I'm afraid I don't know :(

Yep, thats what happens to me as well. If you use nautilus make sure you go to - view - show hidden files

---

