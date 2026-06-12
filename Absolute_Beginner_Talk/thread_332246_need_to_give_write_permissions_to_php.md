---
title: "need to give write permissions to php"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Howlin' Hobbit on 2007-01-05
I'm writing some new php code for my website for the first time since I switched to Ubuntu. I need to allow write permissions for php in one particular folder, and *not* on a file-by-file basis (it needs to be able to create new files in there too).

The folder is /var/www/~hobbit/data. I searched the forums and I'm pretty sure it's something to do with chmod for php as a user (or just adding it to the group) but I see no user named "php" or anything of that ilk via the users and groups section of System/Administration.

How can I do this? I need to be able to test this code *before* it goes up on my web server.

Locally I'm running Apache 2, pretty much "out of the box" (i.e. I haven't done any config tweaking).

Any help appreciated. Thanks!

---

### Post by capitalistpiglet on 2007-01-05
I had a similar problem with php not being able to create directories, the solution is give r/w to www-data.

---

### Post by Howlin' Hobbit on 2007-01-05
Thanks! Now I need to figure out how to do that. As usual, the manual entry just makes my head hurt but I found some info on my earlier search that will help. (Got to learn this anyways!)

---

