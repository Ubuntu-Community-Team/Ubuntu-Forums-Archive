---
title: "gdmsetup being difficult"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-04-11
Actually it's not working at all. When I goto System->Admin->Login Window I'm asked for my root password then...nothing happens

When I try it in the terminal (at least I think it's the same program) it looks like this:

eric@eeee:~$ sudo gdmsetup
Password:
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
eric@eeee:~$ 

It's done this several times in a row. Any ideas?

---

### Post by aysiu on 2007-04-11
A few things you should know, even though none of these is going to solve your problem:

1. When you go to System > Administration > Login Window, you're supposed to enter your user password, not the root password. There is effectively no root password in Ubuntu unless you go out of your way to activate root.

2. When using a graphical application, you should use *gksudo*, not *sudo*: ```
gksudo gdmsetup
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

3. I don't know how that happened to you, but I've seen people get that error before, and if you do a Google serarch on *Failed to connect to socket, sleep 1 second and retry*, you'll see that unfortunately, you're one of few people who have experienced this problem, and more unfortunately there is no known solution to the problem, except to use something else (KDM or WDM) or... reinstall.

---

