---
title: "space not showing up after deleting"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Samip on 2008-03-21
when i delete files using the command: gksudo nautilus, the files that are i deleted do not free up space. i had 2 gigs free and then i made a backup of my installation. after that it said i had no space left on my drive. i deleted the backup after i moved it to a external drive, but it didn't show up that i had regained the space. how do i get the space back onto my hard drive?

---

### Post by iansane on 2008-03-21
You empty trash? If files are on another drive there will be a trash folder created on that drive and it fills up.

---

### Post by Oldsoldier2003 on 2008-03-21
> **Samip said:**
> when i delete files using the command: gksudo nautilus, the files that are i deleted do not free up space. i had 2 gigs free and then i made a backup of my installation. after that it said i had no space left on my drive. i deleted the backup after i moved it to a external drive, but it didn't show up that i had regained the space. how do i get the space back onto my hard drive?

Empty root's trash. When you delete the files as root using nautilus they go to roots trash bin

---

### Post by Nikhil Gohil on 2008-03-21
did you delete them from thje trash???

---

### Post by Samip on 2008-03-21
okay, thanks. i tried going into root and deleting the files from there, and it freed up the space.

---

### Post by Oldsoldier2003 on 2008-03-21
> **Samip said:**
> okay, thanks. i tried going into root and deleting the files from there, and it freed up the space.

Using the command line as root or as a user has the advantage of bypassing the trash bin. rm <filename>( or rm -r <dir name> to delete a directory and all the files and sub directories contained in that dir)

---

### Post by Alnird on 2008-03-22
After seeing this post I came over the idea of trying to view hidden files on my extra HDD, and there it was! If you want to use the grafical interface to clean up any drive that if not your primary HDD first delete the files, then show hidden (CTRL+H) and a new folder will appear called something along the lines of .Trash-username and there lies everything, just enter the folder and delete it all =)

I hope I've helped someone, and not just came with an obvious tip =P

---

### Post by bruce89 on 2008-03-22
Incidentally, you shouldn't delete files outside of /home manually. What were they?

---

