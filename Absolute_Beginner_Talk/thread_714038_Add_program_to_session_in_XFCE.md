---
title: "Add program to session in XFCE"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by altonbr on 2008-03-03
I run GNOME/Ubuntu but on my father's older computer, I've put him on XFCE/Xubuntu. I'm unfamiliar with XFCE and it's underpinning so I was hoping to get some help in regards to sessions.

He's always complaining that his computer is too slow (but doesn't want to buy a new one), so I've installed conky to show him how his computer is reacting to his usage.

The only problem in, in GNOME, it is rather easy to get a program to start up on a new session, but I'm unsure of how to do it with XFCE. Is there a way I can add 'conky -d' to my father's session?

---

### Post by tdrusk on 2008-03-03
I could have sworn there was a sessions section under administration.

---

### Post by aidanr on 2008-03-03
Settings -> Autostarted Applications

or
```
xfce4-autostart-editor
```

---

### Post by altonbr on 2008-03-03
Huh, the program seems to say "failed to write autostart/Conky.desktop". This isn't normal, is it?

---

### Post by aidanr on 2008-03-03
Nope it's not, permissions might be messed up somehow
```
sudo chown -R `whoami`:`whoami` ~/.config/
sudo chmod -R 755 ~/.config/
```

---

### Post by altonbr on 2008-03-03
```
$ chown -R rod:rod .config/ && chmod -R 755 .config/
```

Didn't seem to work. I know what you're doing there, but I don't know enough about XFCE to debug the problem.

What about hacking a file and entering 'conky -d'?

It looks like there is a ~/.config/autostart file, but it is empty.

---

### Post by aidanr on 2008-03-03
I guess you could try to create it manually
```

mousepad ~/.config/autostart/conky.desktop
```
and add:
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Conky
Comment=
Exec=conky -d
StartupNotify=false
Terminal=false
Hidden=false
```

---

### Post by Bruce M. on 2008-03-04
> **altonbr said:**
> I run GNOME/Ubuntu but on my father's older computer, I've put him on XFCE/Xubuntu. I'm unfamiliar with XFCE and it's underpinning so I was hoping to get some help in regards to sessions.

He's always complaining that his computer is too slow (but doesn't want to buy a new one), so I've installed conky to show him how his computer is reacting to his usage.

The only problem in, in GNOME, it is rather easy to get a program to start up on a new session, but I'm unsure of how to do it with XFCE. Is there a way I can add 'conky -d' to my father's session?

Hi altonbr,

I'm a recent convert to XFCE because I have an old computer and it simply runs better. I built my conky under Gnome and ran it automatically.  But with XFCE it took a few days to get it going, because it's a different setup.

To start with I created a hidden file: **.startconky** in my home folder, that looks like this:

```

#!/bin/bash
sleep 20 &
conky -c ~/.conkyscripts/conkymain &
#sleep 1 &
#conky -c ~/.conkyscripts/conkytest &
#sleep 1 &
#conky -c ~/.conkyscripts/conkybl &

```

and made it executable:

```
sudo chmod a+x ~/.startconky
```

As you see above my actual conky script is called **conkymain** and is in the hidden folder; **/.conkyscripts**, the others are for testing. Your naming structure will probably vary, so take note.

Now to start this in XFCE:

[LIST=1]
[*] **Applications > Settings Autostarted Applications**
[*] Click on the **ADD** button:
[*] Name: Conky <<-- anything you want
[*] Description: <<--- anything you want (mine is blank)
[*] **Command:** <<-- see the "*Open Icon*" click on that. When your home folder shows, right click to show hidden files if not visible ... and find the hidden file: **.startconky**. Highlight it and click [ OK ].
[*] Close
[/LIST]

You're done.  Do a [Ctrl]+[Alt]+[Backspace] to restart your session and conky will start in 20 seconds.

Here's the results on my machine:

[CENTER]
[[IMG]http://img129.imageshack.us/img129/4135/screenshotta0.th.jpg[/IMG]](http://img129.imageshack.us/my.php?image=screenshotta0.jpg)
[/CENTER]

Have a GREAT day
CHIMO!
Bruce

---

