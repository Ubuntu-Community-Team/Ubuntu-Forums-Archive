---
title: "Creating a Application Launcher"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-10
I have a .sh file located in **/usr/lib/bc246t-0.8d** the file is called startlinux.sh

I would like to create an application launcher for it and put it either in
applications or just on my desktop. I could be doing this totally wrong. I would
really appreciate some help.

I right clicked on my desktop and choose Create Launcher
A Box comes up.
I then enter this info.

I think that I typed in the wrong Command......
I know that I have to run it from the command prompt
and this is the command **./startlinux.sh**

[IMG]http://img523.imageshack.us/img523/1580/00screenshotqr5.png[/IMG]

---

### Post by SOULRiDER on 2007-08-10
The launcher seems to be ok, I suggest you put that directory in your Home folder, unless its gonna be used by several users.

---

### Post by Orbital75 on 2007-08-10
Sorry, I didn't know until now that you had replied to this in my other thread.
Yep, I tried what you suggested and get the same result.....
humm...... :confused:

---

### Post by SOULRiDER on 2007-08-11
```
/usr/lib/bc246t-0.8d/startlinux.sh
``` should do it, but there may be a permissions issue there, try this and then executing the program:
```
sudo chmod -R +x /usr/lib/bc246t-0.8d 
```

EDIT: its not the cleanest thing to do, but it could help...

---

### Post by Orbital75 on 2007-08-11
Sorry that didn't work either....... Is it possible to created a Launcher for a .sh file?

I even right clicked on the folder to check it's permissions.
I own the folder along with all the files.  I have read,write,and execute permission.

I'm stumped.......  :confused:

---

