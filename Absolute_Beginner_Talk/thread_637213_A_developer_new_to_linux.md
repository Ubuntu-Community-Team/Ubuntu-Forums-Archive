---
title: "A developer new to linux"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by mpiskorz on 2007-12-10
Good day,

First off, thanks for taking a look at my post.  I thought this might be more appropriate in the new user section, but it might be applicable in the development section too.  

I'd like to give a bit of background so you know where I am coming from.

I'm a new linux user that has been developing in Java on Windows.  I've been using Eclipse as well as netbeans.  I'm also using glassfish as an app server. 

I'm trying to get a similar setup on Ubuntu working, and I'm having some problems.  Its my understanding that eclipse 3.3 and netbeans 6.0 is not yet packaged.  When there is a package, everything works great. (Thanks to everyone who as worked on a package!)  When there is not, it gets a bit more completed.

So, now for my questions:

1.  Is there anything that is "wrong" with not using a package?  I understand that ubuntu will more than likely not be able to tell me if something has been updated, but is there anything that might cause system stability issues.  

2.  I've noticed that once I leave the home directory, I'm not able to modify folders unless I do sudo nautilus from a terminal window to bring up nautilus with more privileges.  Is there an easy way I can create a shortcut on the desktop that I can tell it to run it with sudo without having to go to a terminal prompt?  I assume that this process would also work for any application.  An example would be if I wanted eclipse to run as an admin, I could just run it with sudo.  

Thank you for your time.

---

### Post by wormser on 2007-12-10
1.  It is best to use the repositories to get your software.  Somebody else might be should be able to give you more details why.

2.  Create a launcher.  Right click on the desktop> Create Launcher.  Use gksudo instead of sudo for graphical applications.

---

### Post by spiderbatdad on 2007-12-10
i believe...for example, you could change the permissions of eclipse to run for the logged-in user:
```
sudo chmod a+x /location/of/eclipse
```

---

