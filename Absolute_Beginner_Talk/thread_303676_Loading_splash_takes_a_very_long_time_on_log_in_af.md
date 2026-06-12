---
title: "Loading splash takes a very long time on log in after installing Beryl"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-11-20
I just installed Beryl on Ubuntu using this guide:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Every thing is fine, apart from when i log in and that Ubuntu loading splash  takes FOREVER. it stays visible at least 2 - 3 whole minutes after the rest of the screen is loaded.

[[IMG]http://img108.imageshack.us/img108/4278/screenshotwj9.th.png[/IMG]](http://img108.imageshack.us/my.php?image=screenshotwj9.png)

---

### Post by Mr Fat Bat on 2006-11-20
Try removing the line that starts Beryl at startup from /usr/bin/startberyl.sh (Backing it up first)

so /usr/bin/startberyl.sh looks like

> #!/bin/sh
sleep 4
exec gnome-sessionNot

> #!/bin/sh
beryl-manager
sleep 4
exec gnome-session

Then Ctrl+Alt+Bckspce to restart GDM.  Log back in and see if the splash hangs around.  If not then open up a terminal and run [I]beryl-manager. 

[/I]This is just to see if it is beryl that is stuffing up your splash screen.

---

### Post by Jamesbowden on 2006-11-21
I know its Beryl thats doing it because when i log in for a session on regular GNOME its fine.

---

### Post by Jamesbowden on 2006-11-21
/bump

---

### Post by Jamesbowden on 2006-11-21
//bump

---

### Post by Jamesbowden on 2006-11-22
///bump!!!!

---

### Post by marcus2004 on 2006-11-26
Did you ever find a solution to this as it is doing the same thing for me as well. It isn't critical but it is annoying. 
Thanks

---

### Post by Jamesbowden on 2006-11-30
No never found an answer, i just stopped using beryl, because its not just the splash screen that takes along time to load, any other programs that you have loading on start up take along time because they will only load when beryl is done loading.

you can go to  system >> preferences >> sessions, and uncheck the show splash screen on login box, it will still take along time to load, but at leadt you wont see it happening and you can still open firefox or summin while its doing it.

---

### Post by marcus2004 on 2006-12-01
Ok I will do that thank you.

---

### Post by noident on 2006-12-03
I have the same problem too :(
It takes 2-3 minutes, like it's waiting for something to time out.

---

### Post by dm1024 on 2006-12-04
such issue. Any ideas?

btw, if I disable splash on startup, icons are lookink not so cool and apps that are set to start by default (like battery indicator) are loading extremely long.

---

### Post by Eric_T on 2006-12-14
It does the same thing here as well. Pretty annoying, especially since I use kiba-dock, and it won't load until beryl's done loading.

---

### Post by VortexICS on 2006-12-23
I am running Edgy/Beryl on a Thinkpad X40 and I am having the same issue. Nothing critical but it becomes annoying when trying to load startup programs. 
I hope somebody can look into it and come up with a solution.

---

### Post by holli on 2006-12-26
perhaps this might help:
[http://www.ubuntuforums.org/showpost.php?p=1927567](http://www.ubuntuforums.org/showpost.php?p=1927567)

---

