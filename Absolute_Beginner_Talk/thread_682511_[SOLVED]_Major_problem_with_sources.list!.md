---
title: "[SOLVED] Major problem with sources.list!"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by thesqudge on 2008-01-30
ummmm ok i tryed install avant browser with these steps from some site and know i keep getting this every time i try to do just about anything... and i don't no how to fix it because it wont let me install updates or anything...here's what the message keeps saying...

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 80 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

so what did i do? or is there anything to fix this?

---

### Post by oedha on 2008-01-30
sudo gedit /etc/apt/sources.list

see what's on line 80...there must be something here

~E~

---

### Post by mikeyphi on 2008-01-30
Post the contents of /etc/apt/sources.list

---

### Post by JoshuaRL on 2008-01-30
And it's:

```

gksu gedit /etc/apt/sources.list

```

Whenever you want to run a graphical app with root priviledges, use gksu.  It stands for "graphical superuser-do".  If you don't do that, sometimes you can have problems with overwriting important system privilidges.  Just something to keep in mind.

---

### Post by thesqudge on 2008-01-30
WHAT! omg i cant believe i even attempted this, ok the message i keep getting sais it cant read sudo or something to that effect i'm such a noob i don't even know what it was talking about, ok so i deleted the only sudo i could find in the sources.list using nautilus and then it had the same message appear except it used the next word after sudo on the same line ( oh by the way the sudo wasn't on the 80th line even it was above a chuck of urls that actually contained line 80) anywho! so i went back and deleted the whole line that said > sudo tee -a /etc/apt/sources.list and now everything works! i guess that wasn't supposed to be in the file. i probably messed up something when in terminal. but it's fixed now!\\:D/\\:D/\\:D/\\:D/

---

### Post by JoshuaRL on 2008-01-30
Cool.  Yeah, that was definitely wasn't supposed to be there.  That's a terminal command, and has nothing to do with sources.list.

Have fun!  :)

---

