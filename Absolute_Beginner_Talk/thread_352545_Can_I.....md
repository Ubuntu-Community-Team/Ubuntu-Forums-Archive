---
title: "Can I...."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Ki11ah on 2007-02-03
Can I set an openoffice presentation to run on startup, ie. to run automatically when Ubuntu boots up?

---

### Post by moshuptrail on 2007-02-03
I'm sure there's a way to do it at boot-up, but on login is a lot easier. (and more secure)
 Go to System > Preferences > Sessions
and click on the startup programs tab

You'll have to figure out what the correct command line is, but you can add it there.

---

### Post by LostShootingStar on 2007-02-03
I think the best your going to get is using the command:

```

ooffice -impress -show /path/to/presentation/file

```

to get it to start on boot, either put it in  /etc/inint.d/rc.local, or use the gnome session manager

---

### Post by Ki11ah on 2007-02-03
Thanks people, I need it so that the presentation plays as soon as the system boots as the display will be running 24/7. I don't want to have to login to every system(there will be around 10 running) even more so if there is a powercut.

We are currently using xp to do this but need to free up the xp licences as they aren't used for anything else except showing the powerpoint displays.

---

