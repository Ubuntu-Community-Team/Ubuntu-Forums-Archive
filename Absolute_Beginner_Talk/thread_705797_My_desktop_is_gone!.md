---
title: "My desktop is gone!"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by jsnare01 on 2008-02-23
So I installed several updates for various programs and features today and after I rebooted, everything on my desktop was GONE! Please help!

---

### Post by Sam Lars on 2008-02-23
Just the icons, or the background, too?  If you open a file browser window, do they come back?

---

### Post by jsnare01 on 2008-02-23
The icons, the toolbar, everything but the wallpaper.

---

### Post by jsnare01 on 2008-02-23
When I view the desktop directory in the explorer, it says that it's empty.

---

### Post by Daveski on 2008-02-23
> **jsnare01 said:**
> When I view the desktop directory in the explorer, it says that it's empty.

Silly question, but I assume you are still logging in as the same user?

---

### Post by thisismalhotra on 2008-02-23
if you can run syanptic, check if ubuntu-desktop package in installed or not.if no, install that,  If yes remove it and install again, but remember when you will remove it you will have no GUI on your PC just command line... so use terminal,, you can do following commands
```

sudo apt-get remove ubuntu-desktop
```

and once removed run

```

sudo apt-get install ubuntu-desktop
```

**do this only if you are comfortable with command line.**

---

### Post by jsnare01 on 2008-02-23
> **Daveski said:**
> Silly question, but I assume you are still logging in as the same user?

Yes. I only have one user set up.

---

### Post by warbird on 2008-02-23
alt+f2, gconf-editor
Check the status of apps - nautilus - preferences - show_desktop
(should be checked)

---

### Post by jsnare01 on 2008-02-23
I can't get to any programs. I'm in Windows XP now because I can't do anything with Ubuntu at the moment.

---

### Post by jsnare01 on 2008-02-23
In case it might make a difference, I'm dual booting XP and Ubuntu Nautilus.

---

### Post by warbird on 2008-02-23
alt+f2 should bring up the "run" dialog, from which you can, as the name implies, run stuff. did you try what I said?

---

### Post by seventhc on 2008-02-23
even though you can't click on anything, your keyboard commands might still work. You should try as posted above.
*<alt f2> gconf-editor*
or if you want the terminal *<alt f2> gnome-terminal*

---

### Post by jsnare01 on 2008-02-23
[QUOTE=warbird;4391333]alt+f2 should bring up the "run" dialog, from which you can, as the name implies, run stuff. did you try what I said?[/]

I tried that, and it's enabled, but I still can't see anything. I managed to run Firefox from Ubuntu with alt+F2, though.

---

### Post by warbird on 2008-02-23
weird, was almost positive that was the problem... ok, try to run the terminal, "gnome-terminal", then "sudo aptitude reinstall ubuntu-desktop"

---

### Post by jsnare01 on 2008-02-23
> **warbird said:**
> weird, was almost positive that was the problem... ok, try to run the terminal, "gnome-terminal", then "sudo aptitude reinstall ubuntu-desktop"

Okay. Did that. Still nothing. Should I go check the settings again to make sure that it's enabled?

---

### Post by warbird on 2008-02-23
sure, do that, and are you running compiz?
try in the run box "metacity --replace"

edit:
if that doesnt work, open run, and do "gksu users-admin", then add a new user and try logging in with it.

---

### Post by jsnare01 on 2008-02-23
Thanks, warbird. Creating a new user fixed it. :)

---

### Post by warbird on 2008-02-23
great. some config file somewhere must have been messed up. not quite sure what though.

---

