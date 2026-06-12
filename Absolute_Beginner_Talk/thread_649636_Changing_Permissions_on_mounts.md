---
title: "Changing Permissions on mounts"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by stiveni on 2007-12-25
Hello all,

Yesterday i installed again ubuntu after 2 months of working on windows(again). Anyway, what i wanted to do was to share the disks (on the ubuntu machine) to my other PC, where i had Windows on it. I searched the Internet and found that, samba server was the program for this occasion. 

After 1 whole day of trying to install it and setting it up, i finally managed to set it up and get it working too. I made a folder to test if it could do the work, added it to smb.conf and then tried to see if it was accessible from the windows PC. Everything worked! Transferred files successfully!
The problem started when i tried to share my other disks. Those 2 disks are NTFS type (does this matter?).  Anyway, I could see the disks from my windows PC but i coudn't access them, so i tried to see their permissions. The difference was (from the custom folder, i'd successfully shared before) that those disks where in plugdev Group. I tried to change their group by typing:
chgrp root /media/<disk_name>

But they didn't change. Cant understand what's going on, and can't be sure that by changing their permissions, will surely work. Please if you want to ask something, feel free of course and PLEASE HELP ME!!! :lolflag:

---

### Post by stiveni on 2007-12-25
Please:( someone?

---

