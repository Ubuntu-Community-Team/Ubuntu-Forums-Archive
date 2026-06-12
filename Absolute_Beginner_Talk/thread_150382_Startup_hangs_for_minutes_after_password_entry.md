---
title: "Startup hangs for minutes after password entry?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by JEBB on 2006-03-25
Compaq 1688 laptop

I got the Network entries right so that my Zonet now connects to the Internet via my Airport Exteme Base Station with WEP protection.  But now when starting up the computer, after putting in my ID and password, it hangs for a long time.  It does finally get me to the desktop.  Any ideas why?

I was thinking it could be because it is trying to find and connect to all the ipv6 hosts listed in the Network setting.  But otherwise I'm stuck.  Any suggestions would be appreciated.

---

### Post by taurus on 2006-03-25
You can look at your ~/.xsession-error to see what's the problem!

---

### Post by JEBB on 2006-03-26
taurus:  
When I go to terminal and enter:  ~/.xsession-error or /.xsession-error or more /.xsession-error it always returns:  No such file or directory.

Your directions were not sufficiently complete for this rookie.

---

### Post by taurus on 2006-03-26
From a terminal, type
```

more ~/.xsession-errors

```
See if you can spot a trouble in there...

---

### Post by JEBB on 2006-03-26
There appear to be lots of errors.  I obviously have a lot of reading to do to make sense of this.  Can you identify some for me and also point to me some books that cover these responses.  Thanks.   Here is the response:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jim"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/CompaqLinux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/CompaqLinux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/CompaqLinux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/CompaqLinux:/tmp/.ICE-unix/7247

** (gnome-session:7247): WARNING **: Esound failed to start.

** (gnome-session:7247): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command =
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-terminal:7433): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7433): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8543): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8543): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

---

### Post by JEBB on 2006-03-26
I gave up on this.  I figured it was easier to reload the system from the CD then to try to fix whatever was wrong.  The reload worked and the system doesn't hang upon startup.

However, on running more ~/.xsession-errors, I get a list of errors that is pretty much the same as before with a number of additional ones.  What's up??

---

