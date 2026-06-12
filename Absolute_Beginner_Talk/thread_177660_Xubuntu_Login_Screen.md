---
title: "Xubuntu Login Screen"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-16
Is there any way to bypass the login screen and be logged in automatically in Xfce?  There are no other users on this computer, and it's a pain having to enter in my password every time I start the computer.  Also, does Xubuntu HAVE a login screen?  It goes from the Xubuntu boot screen to the kubuntu login screen and then the xubuntu desktop.  I only care b/c the kubuntu login screen is kind of ugly.

---

### Post by aysiu on 2006-05-16
Your profile says you're using Dapper. That means your Xubuntu is using GDM for login. When you're in Xubuntu (logged in), press Alt-F2 and type ```
gksudo gdmsetup
``` There should be an option to automatically log in. There are also options to change the appearance of the login screen.

---

### Post by brady618 on 2006-05-16
mike@Home:~$ gksudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

???

---

### Post by aysiu on 2006-05-16
```
Could not access GDM configuration file
``` That doesn't look good. I'm not sure what to do about that.

---

### Post by aysiu on 2006-05-16
[It looks as if some other people using Fedora have experienced the same problem as you're having](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=Failed+to+connect+to+socket%2C+sleep+1+second+and+retry&btnG=Search). I clicked on the first link, but there was no solution there...

---

