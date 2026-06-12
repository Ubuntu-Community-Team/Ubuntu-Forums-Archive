---
title: "Gtk+ and dbus Error"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by cjdahl60 on 2008-02-05
I left my Ubuntu 7.10 box running overnight.  When I checked it in the morning, the lights on the keyboard were flashing.  Neither the keyboard nor the mouse were active or could wake the system.  I manually powered down and rebooted.  When I logged in, I got an error message that said:

Your session only lasted less than 10 seconds.  If you have not logged on yourself, this could mean that there is an installation problem or that you may be out of disk space.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

View Details (~/.xsession-errors file)




Details displayed when box checked:

(process:4481): Gtk-warning: This process is currently running setuid or setgid.  This is not a supported use of Gtk+.  You must create a helper program instead.  For further details see: [www.gtk.org/setuid.html](www.gtk.org/setuid.html)

Refusing to initialize Gtk+

(process: 4485): Gtk-warning: This process is currently running setuid or setgid.  This is not a supported use of Gtk+.  You must create a helper programinstead.  For urther details see: [www.gtk.org/setuid.html](www.gtk.org/setuid.html)

Refusing to initialize Gtk+

/etc/gdm/xsession: beginning session startup………..
Session-Manager=local/cjdahl60-desktop:/tmp/.ICE-unix/4478
Failed to start message bus: failed to read directory “etc/dbus-1/session.d” no such file or directory
dbus-daemon exited unexpectedly

error: file gsm-dbus.c: line 118 (gsm-dbus-daemon-start): assertion fialed: (dbus-daemon-pid !=0) aborting

I have since logged in fail safe terminal mode and successfully stopped and restarted the dbus process to no effect.  I have also run a sudo apt-get -f install to see if there were any incomplete/aborted install programs.  Everything looked OK.

Any suggestions would be greatly appreciated.

---

### Post by yabbadabbadont on 2008-02-06
What are the permissions on /tmp?  I did a quick search on this and turned up the advice to be sure that /tmp permissions are correct.

```
sudo chmod 1777 /tmp
``` should set them to the correct permissions.

---

### Post by cjdahl60 on 2008-02-10
Thanks for the suggestion.  I went to a fail safe terminal prompt and issued the command you suggested to try to reset the permissions for /tmp.  

I issued the command exactly as you provided and it looks like it was successfully executed, but it had no effect.  I'm still stuck at the same error message when I attempt to log in to the GUI using my ID and password.

Thanks in advance for any other suggestions you may have.

---

### Post by yabbadabbadont on 2008-02-10
Well, if all else fails, you could try reinstalling.  I would do more searching through google for your error messages first though.

---

