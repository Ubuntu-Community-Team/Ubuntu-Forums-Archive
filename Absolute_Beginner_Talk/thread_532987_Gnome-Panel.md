---
title: "Gnome-Panel"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by apb1991 on 2007-08-23
I am typing this from another computer because last time I logged in the panel at the top and the one at the bottom were gone. I can still operate from the desktop and the apps still work but it is hard to acess things such as apps i dont know the command. Could some one give me instructions on how to create a new panel?:confused: thx
PS. when i right click on the desktop and click new app launcher what is the "terminal's" command name?

---

### Post by Dr Small on 2007-08-23
You could try pressing ALT+F2 and typing "gnome-terminal" in the dialog box to open the terminal. From there, I don't know how to get the panel back. I know how to kill it :p

Dr Small

---

### Post by heimo on 2007-08-23
> **apb1991 said:**
> I am typing this from another computer because last time I logged in the panel at the top and the one at the bottom were gone. I can still operate from the desktop and the apps still work but it is hard to acess things such as apps i dont know the command. Could some one give me instructions on how to create a new panel?:confused: thx
PS. when i right click on the desktop and click new app launcher what is the "terminal's" command name?

This is just a guess - but I'd first try to run "killall gnome-panel" (* and then "gnome-panel". Although I've never created new gnome panel "from scratch", so I don't know if this method works.

*) This step just to make sure no panel is running.

---

### Post by Inxsible on 2007-08-23
terminal's command is ```
gnome-terminal
```

---

### Post by asmoore82 on 2007-08-23
'/usr/bin/gnome-terminal'

then see if the panel is running ...

```
~ $ ps -A | grep panel
```

if nothing shows up it is not running so you should run it ...

```
~ $ gnome-panel
```

if it really is gone you need to log out (very important step) and log in to a "failsafe terminal"
and "Nuke" (delete) the panel's configuration to try to restore it to defaults ...

```
[only from "failsafe" terminal]
~ $ /bin/rm -rf .gconf/apps/panel
```

better yet, just move the settings to a backup location INSTEAD of running the previous 'rm' ...
```
[only from "failsafe terminal]
~ $ mkdir .backups
~ $ mv .gconf/apps/panel .backups
```

then logout of the failsafe term with 'exit' -OR- Ctrl+D
and log back in to a gnome session.

---

### Post by apb1991 on 2007-08-23
Thank yall very much

---

### Post by talatnat on 2007-09-03
Thank you asmoore. I just took a break, came back to my computer, and found the gnome-panel centered with all the icons scrunched up... Figuring that there another "panel" to the left (with all the "Add Panel" and "Delete Panel" on a right click), I just happily deleted the panel, and found myself with nothing. Google searches for an hour revealed nothing and I even tried to install Gimme. When that failed, I refined my search, and found your reply, and trusting soul that I am, I tried it to the letter, and lo! behold! I can write to thank you.

This works, for those might face this problem of getting locked out by doing something simple and stupid, and don't know to rewind back...

---

