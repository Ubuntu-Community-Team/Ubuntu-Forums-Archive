---
title: "Problem with Democracy Player"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-19
Hi,

Whenever I turn on Democracy Player a window  pops up saying "An unknown error has occurred while finishing starting up.".  Once I click okay it goes away and nothing happens, but I'll find an occurence of democracyplayer still running in the system monitor.  

This is what I got when I tried to run it in the terminal:

```
zain@ip68-109-35-131Zain:~$ democracyplayer
/var/lib/python-support/python2.5/democracy/eventloop.py:17: RuntimeWarning: Python C API version mismatch for module fasttypes: This Python has API version 1013, module fasttypes has version 1012.
  import database
/var/lib/python-support/python2.5/democracy/frontend_implementation/Application.py:26: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()
DTV: Starting up Democracy Player
DTV: Version:  0.9.2.1
DTV: Revision: unknown
DTV: Loading preferences...
DTV: Restoring database...
Database load slow: 0.480
DTV: Recomputing filters...
failed() called; generating crash report.
WARNING: Error reading logfile: /home/zain/.democracy/log
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/democracy/util.py", line 194, in readLog
    f = open(logFile, "rt")
IOError: [Errno 2] No such file or directory: '/home/zain/.democracy/log'
WARNING: Error reading logfile: /home/zain/.democracy/dtv-downloader-log
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/democracy/util.py", line 194, in readLog
    f = open(logFile, "rt")
IOError: [Errno 2] No such file or directory: '/home/zain/.democracy/dtv-downloader-log'
----- CRASH REPORT (DANGER CAN HAPPEN) -----
App:        Democracy Player
Publisher:  Participatory Culture Foundation
Platform:   gtk-x11
Python:     2.5 (r25:51908, Oct  6 2006, 15:22:41) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu4)]
Py Path:    ['/var/lib/python-support/python2.5/democracy', '/usr/bin', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/PIL', '/usr/lib/python2.5/site-packages/cairo', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0']
Version:    0.9.2.1
Serial:     20061127000
Revision:   unknown
Time:       Sat May 19 19:17:07 2007
When:       while finishing starting up

Exception
---------
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/democracy/app.py", line 531, in finishStartup
    downloader.startupDownloader()
  File "/var/lib/python-support/python2.5/democracy/downloader.py", line 438, in startupDownloader
    cleanupIncompleteDownloads()
  File "/var/lib/python-support/python2.5/democracy/downloader.py", line 405, in cleanupIncompleteDownloads
    for downloader in views.remoteDownloads:
  File "database.pyx", line 496, in database.DynamicDatabase.next
TypeError: exceptions must be strings, classes, or instances, not type

Call stack
----------
  File "/usr/bin/democracyplayer", line 90, in <module>
    startapp()
  File "/usr/bin/democracyplayer", line 57, in startapp
    app.main()
  File "/var/lib/python-support/python2.5/democracy/app.py", line 71, in main
    Controller().Run()
  File "/var/lib/python-support/python2.5/democracy/frontend_implementation/Application.py", line 27, in Run
    self.onStartup()
  File "/var/lib/python-support/python2.5/democracy/app.py", line 512, in onStartup
    self.finishStartup(gatheredVideos)
  File "/var/lib/python-support/python2.5/democracy/app.py", line 674, in finishStartup
    util.failedExn("while finishing starting up")
  File "/var/lib/python-support/python2.5/democracy/util.py", line 131, in failedExn
    failed(when, withExn = True, **kwargs)

Threads
-------
Current: MainThread
Active:
 - MainThread

----- END OF CRASH REPORT -----
/var/lib/python-support/python2.5/democracy/frontend_implementation/gtk_queue.py:109: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/var/lib/python-support/python2.5/democracy/frontend_implementation/gtk_queue.py:129: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
/var/lib/python-support/python2.5/democracy/frontend_implementation/gtk_queue.py:116: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()

```

Seems to be some problem with the downloader not working; the last time it worked the program hung up on me while downloading some files and I forced it to exit--seems like that was the cause but I can't figure out how to fix it.  Reinstalling the program doesn't seem to fix this, and I don't know where all the program's components are saved to try and manually delete everything.  Any ideas?

---

### Post by n8bounds on 2007-05-19
I dont use that app, but if you want to REALLY uninstall something say: sudo aptitude purge foobar  (replacing foobar)

---

### Post by zhinker on 2007-05-19
well, I did what you said and then reinstallled the program using add/remove, but that didn't fix the problem.  Thanks anyways.

---

### Post by n8bounds on 2007-05-22
sorry man, have you tried making a new user and running it from their clean profile?  maybe its some environment setting you have in yours...

---

