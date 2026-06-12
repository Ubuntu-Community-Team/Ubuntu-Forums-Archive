---
title: "[LM]randomnly crashes while broswing"
date: 2012-01-02
forum: Any Other OS
---

### Post by X-jo on 2012-01-02
While browsing, LM11 randomnly crashes and comes back to the login screen.

```
Jan  1 20:24:37 ajo-Satellite-C640 gdm-simple-slave[10773]:  WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or  directory 
Jan  1 20:24:37 ajo-Satellite-C640 acpid: client connected from 10775[0:0] 
Jan  1 20:24:37 ajo-Satellite-C640 acpid: 1 client rule loaded 
Jan   1 20:24:38 ajo-Satellite-C640 gdm-session-worker[10818]: WARNING:  Unable to load file '/etc/gdm/custom.conf': No such file or directory 
Jan   1 20:24:38 ajo-Satellite-C640 rtkit-daemon[1511]: Successfully made  thread 10824 of process 10824 (n/a) owned by '106' high priority at nice  level -11. 
Jan  1 20:24:38 ajo-Satellite-C640 rtkit-daemon[1511]: Supervising 1 threads of 1 processes of 1 users. 
Jan   1 20:24:38 ajo-Satellite-C640 rtkit-daemon[1511]: Successfully made  thread 10832 of process 10824 (n/a) owned by '106' RT at priority 5. 
Jan  1 20:24:38 ajo-Satellite-C640 rtkit-daemon[1511]: Supervising 2 threads of 1 processes of 1 users. 
Jan   1 20:24:38 ajo-Satellite-C640 rtkit-daemon[1511]: Successfully made  thread 10833 of process 10824 (n/a) owned by '106' RT at priority 5. 
Jan  1 20:24:38 ajo-Satellite-C640 rtkit-daemon[1511]: Supervising 3 threads of 1 processes of 1 users. 
Jan   1 20:24:38 ajo-Satellite-C640 gdm-simple-greeter[10817]: Gtk-WARNING:  /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a  GtkWindow 
Jan  1 20:24:39 ajo-Satellite-C640 gdm-simple-greeter[10817]: WARNING: Unable to load CK history: no seat-id found 
Jan   1 20:24:40 ajo-Satellite-C640 gdm-session-worker[10818]:  GLib-GObject-CRITICAL: g_value_get_boolean: assertion  `G_VALUE_HOLDS_BOOLEAN (value)' failed 
Jan  1 20:24:42 ajo-Satellite-C640 gdm-session-worker[10818]: pam_sm_authenticate: Called 
Jan  1 20:24:42 ajo-Satellite-C640 gdm-session-worker[10818]: pam_sm_authenticate: username = [ajo] 
Jan   1 20:24:42 ajo-Satellite-C640 rtkit-daemon[1511]: Successfully made  thread 10936 of process 10936 (n/a) owned by '1000' high priority at  nice level -11. 
Jan  1 20:24:42 ajo-Satellite-C640 rtkit-daemon[1511]: Supervising 4 threads of 2 processes of 2 users. 
Jan  1 20:24:42 ajo-Satellite-C640 pulseaudio[10936]: pid.c: Stale PID file, overwriting.
Jan   1 20:24:42 ajo-Satellite-C640 rtkit-daemon[1511]: Successfully made  thread 10944 of process 10936 (n/a) owned by '1000' RT at priority 5. 
Jan  1 20:24:42 ajo-Satellite-C640 rtkit-daemon[1511]: Supervising 5 threads of 2 processes of 2 users. 
Jan   1 20:24:42 ajo-Satellite-C640 rtkit-daemon[1511]: Successfully made  thread 10945 of process 10936 (n/a) owned by '1000' RT at priority 5. 
Jan  1 20:24:42 ajo-Satellite-C640 rtkit-daemon[1511]: Supervising 6 threads of 2 processes of 2 users. 
Jan  1 20:24:43 ajo-Satellite-C640 nautilus: [N-A] Nautilus-Actions Tracker 3.0.5 initializing...
Jan  1 20:24:43 ajo-Satellite-C640 nautilus: [N-A] Nautilus-Actions Menu Extender 3.0.5 initializing...
Jan  1 20:28:22 ajo-Satellite-C640 kernel: [37382.969520] usb 2-1.1: USB disconnect, address 8
Jan   1 20:39:01 ajo-Satellite-C640 CRON[11600]: (root) CMD (  [ -x  /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] &&  find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin  +$(/usr/lib/php5/maxlifetime) -delete)
Jan  1 20:58:40 ajo-Satellite-C640 NetworkManager[851]: <info> sleep requested (sleeping: no  enabled: yes)
```

Any way to get this fixed?

---

### Post by X-jo on 2012-01-16
bump.. anyone?

---

