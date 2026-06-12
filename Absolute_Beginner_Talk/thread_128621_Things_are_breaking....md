---
title: "Things are breaking..."
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by veritas366 on 2006-02-11
I wrote another thread a few hours ago about how I can't print in firefox anymore.

Now I can't run synaptic.  Here's the error when I try to run it:
> 
Failed to run /usr/sbin/synaptic as user root:
 Unable to copy the user's Xauthorization file.

I don't know what that means or how to fix it.  Any ideas?

---

### Post by astoltz on 2006-02-11
Just try to rename your .Xauthority file (you'll probably have to use sudo):
```
sudo mv .Xauthority Xauthority.old
``` Then log out and back in again.  Should be OK then.

---

### Post by veritas366 on 2006-02-14
[QUOTE=astoltz]Just try to rename your .Xauthority file (you'll probably have to use sudo):
```
sudo mv .Xauthority Xauthority.old
``` Then log out and back in again.  Should be OK then.[/QUOTE]

Well, I did that.  I don't know if it helped or not.  First off, there is no just plain .Xauthority file.  my xsession errors are numerous (this logfile has no date on it???)  Anyway, I noticed I was having gdk issues...a module not loading.  Now, in addition to other woes, the update manager doesn't work.  It doesn't start it's automatic check and when I try to start the program it opens the terminal for a millisecond and then goes away.  Sorry to post all of this file, but there seems to be some gdk related issue and maybe it came about from illadvisedly trying to tweak my desktop following some other threads here.  

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ty"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/ubuntu:/tmp/.ICE-unix/7188
- using device default
- using device default
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
manager.c/2082: mount_all: mounting /dev/hdd
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_label_...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_label_
manager.c/2082: mount_all: mounting /dev/hda1
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_uuid_BE8CAC018CABB1F7...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_BE8CAC018CABB1F7
manager.c/2082: mount_all: mounting /dev/hda2
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_uuid_5075_280C...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_5075_280C
manager.c/2082: mount_all: mounting /dev/hdb1
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_uuid_42c5114d_b260_486d_9fa9_a67c26249c42...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_42c5114d_b260_486d_9fa9_a67c26249c42
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
Error: device /dev/hda2 is not removable
Error: could not execute pmount
Error: device /dev/hda1 is not removable
Error: could not execute pmount
Error: device /dev/hdb1 is not removable
Error: could not execute pmount
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_label_

** (gnome-session:7188): WARNING **: Host name lookup failure on localhost.

(gnome-panel:7333): Gtk-CRITICAL **: gtk_drag_source_set_icon_name: assertion `icon_name != NULL' failed
adding hook target 'source'

(evolution-2.4:7416): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution-2.4:7416): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution-2.4:7416): camel-WARNING **: Could not find key entry for word 'vrxvsfxnws8lljpdxhrxw8xw': Success

  File "/usr/bin/update-manager", line 27, in ?
    import gtk
ImportError: No module named gtk
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
*** attempt to put segment in horiz list twice

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(gnome-panel:7333): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:7333): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(nautilus:7335): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(nautilus:7335): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:7335): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:7335): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)


I can't find in synaptic a "libcdda".  I know "so" is a symbolic link but not sure what it should lead to.  the actual libcdda.so does not exist in the above mentioned folder.  No idea where to get it or how it went away.

---

### Post by Gizmo_RA2 on 2006-09-09
I think I have found the solution to the Xauthority file not working.
> 
sudo cp ~/.Xauthority /root/.Xauthority
sudo chmod 0666 ~/.Xauthority
sudo chmod 0666 /root/.Xauthority
sudo chown root /root/.Xauthority


E-Mail me to let me know if it works or not, I am very interested to know if it is the same problem.

---

### Post by veritas366 on 2006-09-09
I've switched distros twice since that post, but thanks for replying.  Went to simply mepis but 6.0 started using Ubuntu repos....and I started having similar problems.  Something about my system doesn't like the ubuntu repos...

Moved on to PCLinuxOS.  For whatever reason, I've had zero problems.

---

### Post by Gizmo_RA2 on 2006-09-09
sweet thanks for the quick reply :P

---

