---
title: "Gnome"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-03-13
Cheers,

I cant seem to load gnome in a Default Session, all this does is just freeze on the splash screen with no activity at all.

So I have to choose Failsafe Gnome in the login screen, this seems to allow me to boot to gnome but it gives me an error:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in."

what does this mean? also I noticed that my themes are not showing so when I tried to go to System->Preferences->Theme I get another error:

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

Any ideas on how to solve this?

Thanks

---

### Post by louis_nichols on 2007-03-13
If all else fails, you can try deleting the file:

~/.gnome2/sessions

---

### Post by adam.tropics on 2007-03-13
Try logging into failsafe, and add 'gnome-settings-daemon' to the start up programs. You can find them from the menu. System-->Preferences-->Sessions. The try to restart with a normal gnome session.

---

### Post by delphiguy on 2007-03-13
Hi, I dont seem to have 'sessions' in my '~/.gnome' directory.
I did however find 'sessions' in my '~/.metacity' directory.

Whats next?

---

### Post by louis_nichols on 2007-03-13
> **delphiguy said:**
> Hi, I dont seem to have 'sessions' in my '~/.gnome' directory.
I did however find 'sessions' in my '~/.metacity' directory.

Whats next?

Not ~/.gnome but ~/.gnome2

---

### Post by delphiguy on 2007-03-13
yep, I dont have 'sessions' in either .gnome or gnome2.
Also placing gnome-settings-daemon didnt fix the problem.

I also noticed that there is a file called .xsession-errors I dont if this would help 
but here is the content of that file.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "delphiguy"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/zion:/tmp/.ICE-unix/8439

(gnome-session:8439): Gtk-WARNING **: Theme file for ComixCursors-Black-Large has no directories


thanks.

---

### Post by delphiguy on 2007-03-13
I seemed to have fixed it.
I just tried to re-apply my theme and change the icons.

I dont know what happened why suddenly this problem occured, 
but reapplying the themes seems to have fixed it.

thanks for all the help.

---

### Post by dreamsayer on 2007-03-15
> **delphiguy said:**
> Cheers,

I cant seem to load gnome in a Default Session, all this does is just freeze on the splash screen with no activity at all.

So I have to choose Failsafe Gnome in the login screen, this seems to allow me to boot to gnome but it gives me an error:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in."

what does this mean? also I noticed that my themes are not showing so when I tried to go to System->Preferences->Theme I get another error:

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

Any ideas on how to solve this?

Thanks

I had this same problem today. I searched the forums and the net high and low, and tried all of the suggestions mentioned. Nothing worked. Typing gnome-settings-daemon in a terminal gave me a clue. There were a bunch of error messages re: label foregrounds and backgrounds.

So I logged into KDE and selected System Settings & in the Look & Feel section for Appearance, Desktop,Splash Screen & Window behavior I set all of the options contained to their defaults. I logged out of KDE and back into Gnome and Wallah!

I just happened to add KDE to my working Ubuntu system last night. I wanted to try something different. I suspect that the kpersonalizer that runs at first start may have caused this? Just a guess. I re-ran it and was playing around with the different themes. And this was after I successfully logged back and forth between Gnome and KDE without this problem.

---

