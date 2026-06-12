---
title: "change permissions of an entire directory, and its contents"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-01
hi
im trying to make a folder acessable to all users, and its on my desktop
in it are some music files, and i want to make those available to all users, so that guests or other users can listen to them
i dont want to copy the folder into each users sirectory, its 3 gigs and growing
i know its probally something with the ```
 chmod 755 /home/bluefoxx/Desktop/Audio
```
but i tried this, and the files within are un-accessable to the lesser privleged accounts
is there another code i can use?

---

### Post by scxtt on 2007-12-01
chmod -R 755 /home/bluefoxx/Desktop/Audio
```
-R, --recursive
       change files and directories recursively
```

---

### Post by 99bluefoxx on 2007-12-01
thanks for your reply
so do i add that on to the end of my line
also, would the number "775" work as well? i want it acessable only to two other accounts, not to all accounts

EDIT: i didnt fully read your fix on my line, i just glanced at it XD
that answers half my question, lol

---

### Post by scxtt on 2007-12-01
775 would make it **rwx** for the owner and the group, others would just be able to read **r--** ... if you only want specific accounts to have certain access, you could create a new group, put those two people in that group, then do **chmod -R 750 /home/bluefoxx/Desktop/Audio**

rwx for owner
r-- for members of group
--- for everyone else

---

### Post by 99bluefoxx on 2007-12-01
ok thanks much
sorrey to take so long to respond, i have been modding my computer case, putting in a window
im using a dremel, so its rather tedius, XP

---

