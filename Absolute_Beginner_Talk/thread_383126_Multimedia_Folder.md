---
title: "Multimedia Folder"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by anabelle on 2007-03-12
Hi, im writing from a brand new laptop :) that will be used by three people. I have all set up but i want to have multimedia files (music, videos, "shared files") in a common folder. So i don't end up with lots of duplicate stuff...

What is the best way to do it??

---

### Post by nalmeth on 2007-03-12
Not understanding, do you want to do this over a network? Or you just want _3 users with different logins_ to access the same media?

If the latter, what I do is have a separate partition for my Media, that way if I have to, or want to, reinstall, the Media isn't touched.

If you don't want to do this, you could just create a folder in any directory, like /home, or /media, or even just / 
(To create directory in /media or / you must use sudo or root)

Then change the permissions of that folder to be accessible by all users, then put a link to that folder on each users desktop.
(You can do this with gnomes GUI tools, just right click the folder, go to properties -> permissions. It can also be done by the command line)

Am I getting you right?

---

