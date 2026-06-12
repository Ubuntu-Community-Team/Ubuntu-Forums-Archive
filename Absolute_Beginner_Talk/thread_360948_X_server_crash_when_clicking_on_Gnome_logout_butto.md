---
title: "X server crash when clicking on Gnome logout button"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by J.Vega on 2007-02-13
Hi
I recently installed the 64 bit version of Ubuntu (before this, I had the 32 bit version installed) and now I can't really use the logout button in the upper right corner (default). When I click it, my whole X server crashes, throwing me back to the login screen.
I think I had this, too, after installing the 32bit version, but if so, I don't know how I fixed it back there :(

Here are the last lines of my .xsession-errors:
```
alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x5d26d0: Replied to GUI thread
alarm-notify.c:272 (alarm_notify_finalize) - Finalize 
 alarm-notify.c:257 (dequeue_client) - Removing client 0x5c72e0
 alarm-queue.c:2163 (alarm_queue_remove_client) - Posting a task
alarm-notify.c:257 (dequeue_client) - Removing client 0x5d0f60
 alarm-queue.c:2163 (alarm_queue_remove_client) - Posting a task
alarm-notify.c:257 (dequeue_client) - Removing client 0x5d1540
 alarm-queue.c:2163 (alarm_queue_remove_client) - Posting a task
alarm-notify.c:257 (dequeue_client) - Removing client 0x5d49a0
 alarm-queue.c:2163 (alarm_queue_remove_client) - Posting a task
Fenstermanager-Warnung: CurrentTime used to choose focus window; focus window may not be correct.
Fenstermanager-Warnung: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

(nm-applet:7956): libnotify-CRITICAL **: notify_notification_close: assertion `notification != NULL' failed

(nm-applet:7956): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

my Xorg.0.log doesn't show any suspicious warnings or errors, but I can post it as well if it is needed.

---

### Post by J.Vega on 2007-02-19
Apparently I was unable to see the solution because it was too close in front of my eyes ](*,) 
I just had to activate "Ask before logout" in the session preferences of gnome, and the dialog is there now.:roll:

---

