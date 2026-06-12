---
title: "gedit doesn't work for me???"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by tommcd on 2006-05-12
If I try to edit ANY config file with gedit it returns a whole bunch of errors. For example:
sudo gedit /etc/X11/xorg.conf  gives me:

 sudo gedit etc/X11 xorg.conf again, after a long wait I got:
** (gedit:8203): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:8203): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:8203): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (mdi)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDOW (win)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: bonobo_window_flash: assertion `win != NULL' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_add_views: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed
Sometimes I only get a blinking cursor. If I type 
sudo nano (name_of_file) I can edit it. But sudo gedit (name_of_file) just gives either a blinking cursor, or similar errors as above.
Why is this?? Is gedit broken?? Any help appreciated, thanks!!

---

### Post by Gustav on 2006-05-12
does this happen when you run it with ```
gksudo gedit
```?

---

### Post by tommcd on 2006-05-12
If I type:
gksudo gedit /etc/X11/xorg.conf I get a prompt for password followed by:
(gedit:10283): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
What is wrong here?? ANd thanks for the reply.

.

---

### Post by apollyonis on 2006-05-12
Honestly, sounds like something's borked with the file. Just do: 

```
sudo apt-get install gedit gedit-common --reinstall
```

Then try to use gedit - tell me if it fixed it.

---

### Post by tommcd on 2006-05-12
Thanks. I tried your suggestion. I had to insert the Breezy CD in the CD ROM drive. After it finished I tried:
sudo gedit /etc/X11/xorg.conf and I got the same gibberish!
Can't find anything in the forums about this. sudo nano still works though.

---

### Post by Gustav on 2006-05-12
what happens if you run any other gnome app as root from the command line?

---

### Post by steve.horsley on 2006-05-12
I wonder if sonething on your gnome settings is borked. Try to make yourself a new home directory and see if that works. Something like this:

1: Log out of Gnome

2: Change to a console using Alt-Ctrl-F1 and log in

3: Get out of the directory so you can change it:
  cd /home

3: Rename your home directory:
  sudo mv myname myname-backup

4: Make an new empty home directory:
  sudo mkdir myname
  sudo chown myname:myname myname

5: Return to GDM with Alt-Ctrl-F7 and log in again

6: See if gedit is still borked

7: Replace the backup home directory:
  Logout from Gnome
  Alt-Ctrl-F1
  cd /home
  sudo rm -rf myname
  sudo mv mname-backup myname
  alt-Ctrl-F7

If the clean home directory fixed gedit then there must be a problem with a stored setting. Gnome scatters its settings to the four winds, but .gnome, .gnome2, .gconf, .gconfd could be good places to look. If the worst comes to the worst, leave the clean new home there anc copy/move your data files from the backup home directory. I have had to do just that a few times.

---

### Post by garner_nc on 2006-05-12
Install Gvim. It's my editor of choice. You can make it as simple or as complicated as you like.

All the Best,
Doug White

---

### Post by Silentheero on 2006-05-14
I have also got this problem, at least temporarily. I get the same error block and will not open through the CLI but will under the GUI file system. I can use vi but this is bothersome. I will try making a new user folder as suggested and let you know how that works out.

---

### Post by richbarna on 2006-05-14
Gedit(Gnome) is only a text editor, like Kate (KDE), Vim (Most  Distro's) etc

Open the console/ terminal/ konsole etc
type :-
> sudo apt-get install gedit 
or
> sudo apt-get install vim
or
> sudo apt-get install kate

I use vi myself but the choice is yours :)

---

