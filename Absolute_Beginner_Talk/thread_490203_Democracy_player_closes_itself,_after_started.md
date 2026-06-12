---
title: "Democracy player closes itself, after started"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by doldett on 2007-07-02
Hi, guys

I am having problem trying to use democracy player. It closes itself everytimes I open it.

I followed this thread but it does not fix my problem.

[http://ubuntuforums.org/showthread.php?t=484666&highlight=democracy+player](http://ubuntuforums.org/showthread.php?t=484666&highlight=democracy+player)

Please you guys help me out.

Here is the output terminal, if it helps

/usr/bin/democracyplayer.real:81: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  import dbus_bindings
/var/lib/python-support/python2.5/dbus_bindings.py:5: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
/var/lib/python-support/python2.5/democracy/frontend_implementation/Application.py:26: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()
DTV: Starting up Democracy Player
DTV: Version:  0.9.2.1
DTV: Revision: unknown
DTV: Loading preferences...
DTV: Restoring database...
DTV: Recomputing filters...
DTV: Spawning global feed dtv:manualFeed
DTV: Spawning global feed dtv:search
DTV: Spawning global feed dtv:searchDownloads
DTV: Creating channel tab order
DTV: Creating playlist tab order
DTV: Spawning Channel Guide...
DTV: Spawning global feed dtv:directoryfeed
*** Launching Democracy Downloader Daemon ****
DTV: Spawning auto downloader...
DTV: Displaying main frame...
Setting VolumeLevel to 1.0
Icon clear: 0.006
DTV: Starting event loop thread
DTV: Finished startup sequence
/var/lib/python-support/python2.5/democracy/frontend_implementation/gtk_queue.py:109: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/var/lib/python-support/python2.5/democracy/frontend_implementation/gtk_queue.py:129: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
Setting VolumeLevel to 1.0
['/home/kai/.democracy/Movies']
DTV: updating the Guide
*** Daemon ready ***
loaded renderer 'gstrenderer'
DTV: Warning: Bad Header from [http://www.channelfrederator.com:80/rss](http://www.channelfrederator.com:80/rss) (Pragma: )
/var/lib/python-support/python2.5/democracy/frontend_implementation/gtk_queue.py:116: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
WARNING: feed update for: [http://videobomb.com/rss/posts/list](http://videobomb.com/rss/posts/list) too slow (0.157 secs)
WARNING: feed update for: [http://www.channelfrederator.com/rss](http://www.channelfrederator.com/rss) too slow (0.269 secs)
WARNING: feed update for: [http://www.mediarights.org/bm/rss.php?i=1](http://www.mediarights.org/bm/rss.php?i=1) too slow (0.188 secs)
DTV: Warning: Bad Header from [http://www.channelfrederator.com:80/assets/images/album.jpg](http://www.channelfrederator.com:80/assets/images/album.jpg) (Pragma: )
DTV: Warning: Can't process cookie expiration: Mon, 02-Jul-07 11:27:43 GMT
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
downloader: connection closed -- quitting
Shutting down downloaders...

---

### Post by quicksilver1024 on 2007-07-08
i get the some error...

---

### Post by tro on 2007-07-18
update-alternatives --config java
switch to java 6, if you have it. I had to restart before the changes took effect. Although miro still seems to be using java 5, the error is gone and it works now.

---

### Post by chadlewis on 2007-07-18
I'm getting the same error. Switching to 6 did not fix the problem.

---

### Post by chadlewis on 2007-07-18
Ok this is *really* hack, but if you absolutely need it to work, shut off your internet connection and launch Miro, then switch to a screen other than the "Miro Guide". Something on that screen is causing the crash.

---

### Post by chadlewis on 2007-07-18
This worked for me - [http://ubuntuforums.org/showthread.php?t=504047&highlight=miro](http://ubuntuforums.org/showthread.php?t=504047&highlight=miro)

---

### Post by tro on 2007-07-18
It crashes for me whenever I try to play anything:

```
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 42 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I'm guessing miro calls xine without reading my .xine/config, which specifies that I need the OpenGL video driver and not the "auto" one. I have no idea how to fix it, though.

---

### Post by p_quarles on 2007-07-18
I got it to get as far as playing videos by installing this: ```
sudo apt-get install libxine-extracodecs
```
Unfortunately, now it crashes immediately after the video is done. A little better, at least.

---

### Post by deadlikeoscar on 2007-07-18
Democracy is now named Miro. If you go to their site under downloads you can find instructions to enable their repository. That may solve your problems as Synaptic should find all dependencies and make it a smooth process.

---

### Post by p_quarles on 2007-07-18
In my case, actually, the problems started *after* I upgraded to Miro.

---

### Post by deadlikeoscar on 2007-07-18
Nice...:) Sorry to hear that.

---

### Post by tro on 2007-07-18
> **p_quarles said:**
> I got it to get as far as playing videos by installing this: ```
sudo apt-get install libxine-extracodecs
```
Unfortunately, now it crashes immediately after the video is done. A little better, at least.

Thanks, but that didn't help as I already had libxine-extracodecs installed.

---

### Post by APer3Caper on 2007-12-15
I was able to stop Miro from crashing by simply uninstalling the Sun Java 6 plugin.

Just go into the terminal and type
```
sudo apt-get remove sun-java6-plugin
```

When you fire up Miro it shouldn't crash. Hope this helps someone.

UPDATE: I just tried playing a video. It played for two seconds and the video stopped. Miro didn't close, but the video won't play plus I don't think the sound is working. Maybe this is just an error on my part and that uninstalling the Java plugin does actually work.

---

### Post by jKeats3 on 2008-03-24
APer3Caper, thank you so much for this solution...it worked perfectly for me.  Now, I wonder what the conflict is between the java6 plugin and Miro.

---

