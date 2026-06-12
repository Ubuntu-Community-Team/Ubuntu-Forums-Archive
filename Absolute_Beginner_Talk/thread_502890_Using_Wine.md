---
title: "Using Wine"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by msnealer on 2007-07-17
Can someone tell me how to configure Wine, so that I can install programs that can be used by all users on the system.  The set-up I have just installs them for whatever user runs the commands

---

### Post by 3rdalbum on 2007-07-17
Take your ~/.wine directory and put it into /etc/. Open up a terminal and type the following:

```

cd /etc/
sudo chmod -R a+rwx .wine/

```

Now, for all users that currently exist on your computer, you should create symbolic links in their home directories to /etc/.wine

You can do this through the root file browser; you middle-click-drag the /etc/ directory into the home directory of each user, then select "Link here".

Finally, add a symbolic link to /etc/.wine to /etc/skel/

I have not tried this, but it should work the way you want. All users will be able to access the shared .wine directory, including Wine itself. If you add users to the computer, they will automatically be able to access the shared .wine directory too!

---

### Post by msnealer on 2007-07-17
Just to add to this.  I put a game on wine for my wife to use and yesterday it was working. Now after a single reboot it has stopped working.  

The program starts and resets the screen resolution and then crashes. No messages, or anything

---

### Post by jodoj80 on 2007-07-18
3rdalbum when I try ```
cd /etc/
sudo chmod -R a+rwx .wine/
``` it says ```
chmod: cannot access `a+rwx': No such file or directory
chmod: cannot access `.wine/': No such file or directory
``` it ask me the password and I wrote the root user password that is the same password that I use for my user.

---

### Post by Malta paul on 2007-07-18
Hi, this may help you:[http://www.winehq.org/site/getting_help:](http://www.winehq.org/site/getting_help:))

---

### Post by Malta paul on 2007-07-18
Sorry the link gives an error 404. (in previous post)
This should be ok   [http://www.winehq.org/site/getting_help:](http://www.winehq.org/site/getting_help:)

---

