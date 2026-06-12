---
title: "gedit error"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by pshnfry on 2006-05-09
Hi, can anyone assist with deciphering this error string recieved when starting gedit:

peter@ubuntu:~/Desktop$ sudo gedit
Password:

** (gedit:8197): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

** (gedit:8197): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8197): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8197): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

(gedit:8197): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>'  in cast to `GObject'

(gedit:8197): GLib-GObject-WARNING **: instance of invalid non-instantiatable ty pe `<invalid>'

(gedit:8197): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TY PE_CHECK_INSTANCE (instance)' failed

(gedit:8197): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>'  in cast to `BonoboMDI'

** (gedit:8197): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (md i)' failed

** (gedit:8197): CRITICAL **: gedit_file_new: assertion `ret != FALSE' failed


gedit appeared to hang when using the command:
sudo gedit interfaces
I obviously didn't wait for error messages long enough and closed down the terminal window.  Tried removing the gedit package and re-installing via synaptic in case of corruption. Then typed in the command shown at the top of this post and left it for an extended period - came back to see this error string.

Tried searching the forum for "gedit:8197" and "gedit_prefs_manager", no results returned.

Any tips?

---

### Post by aysiu on 2006-05-09
Use ```
gksudo gedit
``` *sudo* is for terminal applications and commands, not graphical applications.

---

### Post by pshnfry on 2006-05-09
Until tonight I had used sudo.

Using gksudo I get this:

peter@ubuntu:~/Desktop$ gksudo gedit
(gedit:8371): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

There may be more, it appears to have hung but I'll leave it to run and post again if any more detail is provided.

---

### Post by aysiu on 2006-05-09
Do you get that error and it works... or you get that error and it doesn't work?

Sometimes when you launch commands from the terminal, you get a lot of output, but it doesn't necessarily mean something's wrong.

---

### Post by pshnfry on 2006-05-09
Error, some delay, then works. Thank you.

Any thoughts on why sudo gedit worked previously?

---

### Post by aysiu on 2006-05-09
[QUOTE=pshnfry]Error, some delay, then works. Thank you.

Any thoughts on why sudo gedit worked previously?[/QUOTE] *sudo* will appear to work for a lot of graphical applications (the most notable exception is the text editor Kate in KDE), but it's possible that using *sudo* with a graphical application will affect some permissions in your /home files. It's safest to use *gksudo* instead.

---

### Post by trent dillman on 2006-05-09
...

---

### Post by ac1968 on 2006-09-05
Im pretty hopeless at this but i found something that worked for me.

When i got this error i was in a root terminal session trying to open a plain text file created by user XY.

When i opened up a plain terminal session as user XY (owner and original creator of the file) I didn't get this error and got straight into the file.

hope this helps.

AC.

---

