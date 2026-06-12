---
title: "gnome error on start"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by n00rt on 2008-02-08
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-vviJcsK3uX: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.



- anyone have a clue as to how this may be fixed?  when it happens my windows partition isn't mounted and sometimes the background picture disapears - everything else seems to work but then the x thing will sometimes crash and restart.

usually cntrl, alt & backspace will clear the problem but how can i stop it from occurring?

---

### Post by jasmuz on 2008-02-08
When you login into Gnome, can you run the gnome-settings-daemon in the terminal, does it work?

If so, just add the gnome-settings-daemon to the session startup:
System--->Preferences----->Session----->Startup programs.

---

### Post by spiderbatdad on 2008-02-08
This is not a serious error. It is usually the result of some conflict between the gnome-settings-manager and some xserver session enabled for gl rendering (compiz). Your error looks like a modem was trying to be accessed for the session...not sure. It is an annoyance, I know. Maybe look through daemon log for more information on what is happening. Maybe at login set xsession, and use it every time.

---

### Post by NewDisciple on 2008-02-08
I have been getting the same error as you for the last 3 or 4 days.  Never had this in the past and I have had Ubuntu since Breezy.  Sometimes I have to reboot up to three times to get Gnome to work correctly.  This will certainly be a pleasure the first time I have to do a presentation and then have a Gnome error.  Oh yeah, I guess I have a presentation tonight as a matter of fact,  Can't wait for that.

---

### Post by n00rt on 2008-02-08
thanks for the info - i think that bizarrly it may have something to do with my wireless card - ubuntu edgy always used to hang during startup if the wireless switch was turned off - it 'll start up now in gutsy but this seems to happen if i switch the wireless off and then restart

doesn't seem logical - but then - weirder things have happened

---

