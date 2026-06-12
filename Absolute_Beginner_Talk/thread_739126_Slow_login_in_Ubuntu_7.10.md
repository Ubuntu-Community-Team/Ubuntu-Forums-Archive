---
title: "Slow login in Ubuntu 7.10"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by acrimotel on 2008-03-29
Hello,
I have been reading some other threads about my problem, but I cannot find a solution.. I have Ubuntu 7.10 and the time of login (time from filling in my user and pw until desktop is visible) is long.. about 2 minutes.
I have seen in a thread that I could check the file .xsession-errors for possible problems but I don't understand anything of what it says. I have attached this information..
Any ideas?
Thank you!!






(process:5275): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5279): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
SESSION_MANAGER=local/rosa:/tmp/.ICE-unix/5272
** Message: Not starting remote desktop server
Checking for Xgl: not present. 


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
I/O warning : failed to load external entity "/home/rosa/.gnome2/gedit/sessions/gedit-C1h2sB"
Detected PCI ID for VGA: 01:05.0 0300: 1002:4337 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: Throttle level is 0
present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
evolution-alarm-notify-Message: Setting timeout for 36502 1206835200 1206798698
evolution-alarm-notify-Message:  Sun Mar 30 00:00:00 2008

evolution-alarm-notify-Message:  Sat Mar 29 13:51:38 2008

evolution-alarm-notify-Message: Setting timeout for 36502 1206835200 1206798698
evolution-alarm-notify-Message:  Sun Mar 30 00:00:00 2008

evolution-alarm-notify-Message:  Sat Mar 29 13:51:38 2008

Initializing gnome-mount extension
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Sun Mar 30 00:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rosa/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rosa/.evolution/calendar/local/system - Calendar Open Async... 0x80c5ed0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80db560
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rosa/.evolution/tasks/local/system 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rosa/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rosa/.evolution/memos/local/system - Calendar Open Aalarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Sun Mar 30 00:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rosa/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rosa/.evolution/calendar/local/system - Calendar Open Async... 0x80c8cd0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rosa/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rosa/.evolution/tasks/local/system - Calendar Open Async... 0x80db310
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/rosa/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/rosa/.evolution/m
(evolution-alarm-notify:5350): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
emos/local/system - Calendar Open Async... 0x80e0930
  PID TTY          TIME CMD

(gnome-panel:5326): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -20 and height 25
The application 'gedit' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
rm: cannot remove `/root/.gnome2/gedit/sessions/gedit-C1h2sB': Permission denied
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0xa9516e8]
** Message: Init mimetype 'video/x-msvideo' mode 2
** Message: Base URI is 'http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi'
** Message: Real mimetype for 'video/x-msvideo' is 'video/x-msvideo'
argv[0] type video/x-msvideo
argv[1] src [http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi](http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi)
argv[2] name plugin
argv[3] height 100%
argv[4] width 100%
** Message: mSrc: [http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi](http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi)
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.13) Gecko/20080325 Ubuntu/7.10 (gutsy) Firefox/2.0.0.13 --mimetype video/x-msvideo 
** Message: Viewer spawned, PID 5733
** Message: GetValue variable 14 (e)
** Message: Initial window set, XID 1c11fe4 size 1013x537
** Message: No viewer proxy yet, deferring SetWindow
** Message: NewStream mimetype 'video/x-msvideo' URL 'http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi'
** Message: Not expecting a new stream; aborting stream
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_5733'
** Message: NameOwnerChanged old-owner '' new-owner ':1.19'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
** Message: NameOwnerChanged old-owner '' new-owner ':1.19'
** Message: Already have owner, why are we notified again?
Viewer: SetWindow XID 29433828 size 1013:537
sh: jackd: not found
** Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
** Message: IsSchemeSupported scheme 'http': yes
** Message: totem_embedded_open_internal 'fd://0' is-browser-stream 1 start-play 1
** Message: BEFORE _open
** Message: AFTER _open (ret: 1)
** Message: Viewer state: PLAYING
** Message: OpenStream reply
** Message: NewStream mimetype 'video/x-msvideo' URL 'http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi'
** Message: Is unsupported mime-type 'video/x-msvideo'
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097f18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097f18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarok: WARNING: Pixmap not found for mimetype application/ogg
sync... 0x80e0c70
alarm-notify.c:393 (cal_opened_cb) file:///home/rosa/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e1940: Received at thread b4d62b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c5ed0
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e1940: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/rosa/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80ddbd0: Received at thread b4d62b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80e0c70
alarm-queue.c:581 (load_alarms_for_today) - From Sat Mar 29 13:51:54 2008
 to Sat Mar 29 13:51:54 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80ddbd0: Replied to GUI thread
alarm-queue.c:1832 (check_midnight_refresh)
alarm-queue.** Message: Viewer state: STOPPED
** Message: StreamAsFile filename '/home/rosa/.mozilla/firefox/fesrb12j.default/Cache/AB94D2D5d01'
** Message: mBytesStreamed 60738974
** Message: DestroyStream reason 0
** Message: URLNotify URL 'http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi' reason 0
** Message: totemPlugin dtor [0xa9516e8]
** Message: NP_Shutdown

---

### Post by Hutom on 2008-03-30
I installed Ubuntu 7.10 in a laptop. Had the same problem. Reinstalled it. It is working fine now.

---

