---
title: "Permission problem"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by dudeeh on 2006-11-02
Here is my situation: i have 1 desktop computer (ubuntu) and 1 laptop (windows)
Now on this desktop i have  a map that i share over samba so i can access it from my laptop. On the desktop i have 2 users: user1 and user2. User1 is the one created when setting up ubuntu, thus my standard user. User2 was created for security reasons and _only_ has rights on that specific shared folder.
User1 and user2 are in the same group and i set the sticky bit on shared folder, so it gets the correct group etc. Now my problem is the following: suppose im working on my desktop computer with user1 and i browse (nautilus) to the shared folder, create a new file, it gets the wrong permissions. 
It should have -rwxrwx---, but instead it gets -rw------- (the x lacking probably cause its a text file im creating, but that isnt too important atm)
my main problem is that the group has no access to the file, hence user2 has no rights over it.

I have been doing some research and everything points in the general direction of umask. But can i set umask for one specific folder (and subfolders) ? Or can it only be set per user?
Either way, what would the command be? I tried "umask 0002" (default is 0022) which "should" create files with all permissions for the group. No such thing, it gave me the same permissions as before.

So what am i doing wrong? How can i have the permissions be inherited (also note that this has to work through samba)

---

