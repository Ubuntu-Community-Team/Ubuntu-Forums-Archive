---
title: "Hot to turn off Desktop Effects without gui?"
date: 2007-05-11
forum: Apple Intel Users
---

### Post by MirrorMask on 2007-05-11
Hi.
Yesterday  I've installed my copy of UBUNTU 7 on my MacBookPro with Parallels. After installation (fine, UBUNTU appears to be very intresting :KS ) I've tried Desktop Effects and BANG, screen is blank!
I've tried to restart, but everytime, after, login, screen become all white again (I can see no cursor, can't make anything).

Can I turn off Desktop Effects without GUI?

Please, someone can help me????

:confused:

---

### Post by lehenryjr on 2007-05-15
I am having the same issue. I can't do anything on the system. It's hosed.
It's booting, I login and then poof - white screen can't do crap. I can't even reboot properly.

I don't want to reinstall, but damn where's the recovery for this?

I see tons of articles on how to turn 'desktop effects on', but how the hell do you turn it off with no user interface?

Where's the safe mode, where's the undo, where's the test video mode? I have had Ubuntu for about 4 months, with no issues, now I turn the desktop effects on and damn if I can't revert back to be able to do anything.

yeah, I'm frustrated.

I can't believe no one has had this issue.

Thanks,
LH

---

### Post by benanzo on 2007-05-15
I can't remember specifically but I think the compiz startup script is kept in $HOME/.config/autostart

You can navigate to that dir in terminal and delete the appropriate .desktop file, then try logging in again.

---

### Post by duffman25 on 2007-05-16
> **benanzo said:**
> I can't remember specifically but I think the compiz startup script is kept in $HOME/.config/autostart

You can navigate to that dir in terminal and delete the appropriate .desktop file, then try logging in again.

You can probably try to login into gnome's failsafe session. You can choose the session from GDM (login screen). See if that helps to find where desktop effects is launched at startup.

EDIT: found. The setting is stored in /desktop/gnome/applications/window_manager/default in gconf. You should probably have to either modify it via gconf-editor (in failsafe) or changing the key via command line (which is possible see: [http://www.gnome.org/learn/admin-guide/latest/gconf-6.html](http://www.gnome.org/learn/admin-guide/latest/gconf-6.html))

hope this helps.

---

### Post by godd4242 on 2007-05-16
> **duffman25 said:**
> You can probably try to login into gnome's failsafe session. You can choose the session from GDM (login screen). See if that helps to find where desktop effects is launched at startup.

EDIT: found. The setting is stored in /desktop/gnome/applications/window_manager/default in gconf. You should probably have to either modify it via gconf-editor (in failsafe) or changing the key via command line (which is possible see: [http://www.gnome.org/learn/admin-guide/latest/gconf-6.html](http://www.gnome.org/learn/admin-guide/latest/gconf-6.html))

hope this helps.

Speaking to that, there has to be a Compiz command for shutdown via terminal.
I've never used Compiz though, so I might be completely incorrect.

---

### Post by lehenryjr on 2007-05-16
**Solution**:
And thanks to everyone!

Booted into Ubuntu, 
selected Terminal Service and logged in.
In terminal window get in to the gconf-editor (in failsafe mode) (type: gconf-editor @ command line/Enter) 
I navigated to the /desktop/gnome/applications/window_manager/

There's two keys(entries) that need to be removed (just delete the contents of default and current).
**Current**: USR/BIN/COMBIZ
**Default**: USR/BIN/COMBIZ

After making the changes, exit the gconf-editor.
and enter exit (to exit terminal)

Your asked to login again, everything is fine. 
Back to normal.

Again, thanks for everyones help.
LH

---

### Post by llorrac on 2007-12-12
If you're using XGL, you can disable it from startup by creating this file.

~/.config/xserver-xgl/disable

This should sort you out.

---

