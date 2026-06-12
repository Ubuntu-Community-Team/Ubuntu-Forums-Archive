---
title: "Kde startup programs"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-20
okay how can i add like kwifimanager on startup with kde 3.5 if yall could please help thanks

---

### Post by fedex1993 on 2008-01-20
i know there is a way to add start up programs i jsut dont know how to yet on kde please help

---

### Post by bwtranch on 2008-01-20
Howdy,

You can install KDE along with Gnome on your desktop. It can get a little confusing, though. But KDE has a lot more programs to play with. And I like some of the K programs better.

If you want to try this:

sudo apt-get install kde

I think that's it, haven't done that since 7.04 and make sure your dependencies are up. Use Synaptic is the easy way. Let me know if you have any problems.

---

### Post by Christmas on 2008-01-20
You have to put your your startup scripts into your ~/.kde/Autostart directory, where ~ is your home directory i.e. /home/your_user/kde/Autostart. The script may be something like:
```
#!/bin/bash

/usr/bin/kwifimanager
```
Or where your kwifimanager binary is located (do a 'whereis kwifimanager' to see). Don't forget to make your script executable (chmod 755 myscript.bash). Next time you start KDE, Kwifimanager should start automatically.

---

### Post by bwtranch on 2008-01-20
Re #4 you don't have to do that!!! All you have to do is install the KDE Desktop.It'll run.

---

