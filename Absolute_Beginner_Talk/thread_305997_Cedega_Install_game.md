---
title: "Cedega: Install game"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by cold-peak on 2006-11-24
Hi all,

Using: Ubuntu 6.10 (Edgy Eft)

i have a subscription with Cedega, and it installed correctly, updated, downloaded the engine, passed all the tests etc etc etc

However; when i go to install a game it gives me a few problems. It happily creates the directory and name in the cedega directory and program, however the install fails to start...

When i try and run from the terminal i get this:

```


conrad@KUSARI:/media/Fix/WoW-1.12.0-enGB-Installer$ sudo cedega Installer.exe
wine: Unhandled exception, starting debugger...


```

and with root

```


root@KUSARI:/media/Fix/WoW-1.12.0-enGB-Installer# sudo cedega Installer.exe
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2379, in ?
    Point2Play_ref = Point2Play.Point2Play( config_file )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 352, in __init__
    config_file.readfp( file( filename, "r" ) )
IOError: [Errno 2] No such file or directory: '/root/.cedegarc'
root@KUSARI:/media/Fix/WoW-1.12.0-enGB-Installer# 


```

any ideas?

---

### Post by cisforcojo on 2007-02-08
I am having similar problems but mine originally worked, but now is focked.
YOUR problem looks like it results from how you installed it. My guess is that you installed it not as root but as a user. The .cedegarc file is probably in your /home/username 

Check that out. You're running cedega from root now and that's why .cedegarc isn't in your /root path.

Hope this helps.

---

### Post by meng on 2007-02-08
You shouldn't have to 'sudo' to install within Cedega.

---

