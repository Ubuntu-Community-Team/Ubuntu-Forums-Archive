---
title: "Automatic Login"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-22
I'm trying to setup an automatic login in xfce following this thread: 

[http://www.ubuntuforums.org/showthread.php?t=152274](http://www.ubuntuforums.org/showthread.php?t=152274)

However, every time I get to the command: 

sudo gcc-3.4 -o autologin autologin.c

I get this:

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status


I can't figure it out.  Of course, I am a n00b, so that pretty much sums it up.  Also, it says in the how-to that I should search for the file 1:2345:respawn:/sbin/getty 38400 tty1.  What command should I use for that?  I am using Dapper, and this might have been written for Breezy, so maybe that's the problem?  If it is, is there any way around it?  Thank you in advance for any input.

---

### Post by aysiu on 2006-05-23
Any reason you don't just use GDM?

---

### Post by skippy81 on 2006-05-23
> /usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Have you installed GCC 3.4 yet?  You need to use a package manager and download 3.4 and its dependancys.  I believe ubuntu only ships with version 4.0.

> 1:2345:respawn:/sbin/getty 38400 tty1

Looks like a line from /etc/inittab to me. You can open this file for editing by opening a terminal and typing:

> sudo gedit /etc/inittab

I suggest you use a "#" symbol to commend the line out rather than delete it, incase you make a bad change and want your old line back.  

I did a similar thing with gnome and took my GDM out of the picture.  However the downside of it is that you can't use the reboot and shutdown functions from within x.   This means that the few seconds you save on boot get wasted by having to to open a terminal and manually shut down.  I guess it will free up a bit of ram though. 

If your only aim is to skip out having to enter a password everytime you start your PC, then you can configure the GDM to automatically sign you in, thats how I now have Gnome GDM setup.

---

### Post by adam.tropics on 2006-05-23
> However the downside of it is that you can't use the reboot and shutdown functions from within x.

Sure you can. 
```

Sudo visudo
```

password, then it will open nano. add to the file
```

User_Alias USERS = adam
Cmnd_Alias SHUTDOWN = /sbin/shutdown
USERS ALL = NOPASSWD: SHUTDOWN

```

replace 'adam' with you user name.

Save it <ctrl>o ,good to go, you can create a panel launcher to restart using

```
sudo shutdown -r now 
```

or shutdown using


```
sudo shutdown -h now 
```

---

