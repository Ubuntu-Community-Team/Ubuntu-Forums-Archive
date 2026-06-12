---
title: "MySQL server's socket is not correctly configured"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by useLinux, on 2007-05-04
After everything for my server works, and i installed, this comes up when i try to login to phpmyadmin or do anything in shell with the database.

Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

It was working before, becuase i logged into phpmyadmin and created databases (testing it) then when i tried it again like 4 - 5 days later it just didnt work. :S

Ive tried looking at like FAQ's and community documentation but i cant seem to be able to fix it. Any ideas?

[Thanks for all those who help]

---

### Post by useLinux, on 2007-05-04
Just moving it up to the top so someone will post xD

---

### Post by elglas on 2007-05-09
I believe the problem is caused by an update to mysql in fiesty, and seems to be permission oriented.

I dont even have a mysqld.sock file after installing with apt?

maybe someone can lend us a hand

---

