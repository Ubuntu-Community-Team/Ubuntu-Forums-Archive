---
title: "Democracy Player closes itself after a few secs"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by quicksilver1024 on 2007-07-21
Hi,

I have been neglecting my problem with Democracy Player for quite some time now, but now I want to finally fix it!
After a few seconds of launching the program, it closes itself and gives the following error:

WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
TIMING   gtkAsyncMethod: <function _gtkInit at 0x8a9b4c4> took too long: 5.352
alsa
oss
pulseaudio
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a345dc> took too long: 4.381
TIMING   gtkSyncMethod: <function getDisplay at 0x8a9b6bc> took too long: 4.423
INFO     got file:///tmp/tmpJiCVVM.html
TIMING   Icon clear: 9.504
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (34.613 secs)
TIMING   idle (Finishing startup) cumulative is too slow (34.613 secs)
TIMING   gtkAsyncMethod: <function selectDisplay at 0x8a9b64c> took too long: 9.532
INFO     got file:///tmp/tmp3-sCz1.html
TIMING   timeout (Feed update (Feedless Videos)) too slow (0.609 secs)
TIMING   gtkAsyncMethod: <function fillMovieData at 0x8a3464c> took too long: 1.456
TIMING   timeout (Save database) too slow (3.472 secs)
TIMING   gtkAsyncMethod: <function fillMovieData at 0x8a3464c> took too long: 1.162
INFO     *** Daemon ready ***
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
TIMING   WARNING: Calling <bound method HTTPDownloader.onHeadersRestart of <dl_daemon.download.HTTPDownloader instance at 0x82e746c>> on HTTPClient: [http://www.ragtagfilms.net/wngpodcast/morningafter.mp4](http://www.ragtagfilms.net/wngpodcast/morningafter.mp4) too slow (0.573 secs)
TIMING   gtkAsyncMethod: <function fillMovieData at 0x8a3464c> took too long: 2.826
TIMING   WARNING: Calling <function <lambda> at 0x9da4d14> on HTTPClient: [http://youtube.com/img/pic_youtubelogo_123x63.gif](http://youtube.com/img/pic_youtubelogo_123x63.gif) too slow (5.794 secs)
TIMING   idle (Start Downloads) too slow (0.521 secs)
TIMING   timeout (Save database) too slow (1.428 secs)
TIMING   WARNING: Calling <function <lambda> at 0x9da50d4> on HTTPClient: [http://ted.streamguys.net/TEDTalksvideo_tile.jpg](http://ted.streamguys.net/TEDTalksvideo_tile.jpg) too slow (0.960 secs)
TIMING   feed update for: [http://feeds.feedburner.com/comedycentral/motherload](http://feeds.feedburner.com/comedycentral/motherload) too slow (0.436 secs)
TIMING   feed update for: [http://abcnews.go.com/xmldata/xmlPodcast?id=1478958&src=i](http://abcnews.go.com/xmldata/xmlPodcast?id=1478958&src=i) too slow (0.136 secs)
TIMING   WARNING: Calling <function <lambda> at 0x9da51b4> on HTTPClient: [http://podcast.msnbc.com/audio/podcast/images/pdv_nn_netcast.jpg](http://podcast.msnbc.com/audio/podcast/images/pdv_nn_netcast.jpg) too slow (1.926 secs)
TIMING   feed update for: [http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml](http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml) too slow (0.520 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - [http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml](http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml))) too slow (0.625 secs)
TIMING   feed update for: [http://www.discovery.com/radio/xml/sciencevideo.xml](http://www.discovery.com/radio/xml/sciencevideo.xml) too slow (0.425 secs)
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

I uninstalled Democracy player to install Miro (the 'newer' DP) to see if it would fix my problem, but it didn't.

Any help is appreciated thanks.

---

### Post by p_quarles on 2007-07-21
Miro is buggy under Ubuntu. I got it working a lot better, though, by editing the file
/usr/share/python-support/miro/miro/frontend_implementation/VideoDisplay.py

Uncomment the line that says```
self.add_renderer("gstrenderer")
```
And then comment out the line that says```
self.add_renderer("xinerenderer")
```
And, obviously, if you aren't sure how to do this, just ask.

---

### Post by quicksilver1024 on 2007-07-22
Nope, doesn't work.

quicksilver@quicksilver-laptop:~$ miro
/usr/bin/miro.real:84: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

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
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 93, in <module>
    startapp()
  File "/usr/bin/miro.real", line 60, in startapp
    app.main()
  File "/var/lib/python-support/python2.5/miro/app.py", line 78, in main
    platformutils.setupLogging()
  File "/var/lib/python-support/python2.5/miro/platformutils.py", line 71, in setupLogging
    filemode="w")
  File "/var/lib/python-support/python2.5/miro/__init__.py", line 1240, in basicConfig
    
  File "/var/lib/python-support/python2.5/miro/__init__.py", line 770, in __init__
    
IOError: [Errno 13] Permission denied: '/home/quicksilver/.miro/miro-log'

---

### Post by p_quarles on 2007-07-22
It looks like you might have some out of date Python libraries. Try updating your packages:
```
sudo apt-get update
sudo apt-get upgrade
```
I don't know if that will help, but it's worth a try.

---

### Post by Holzster on 2007-07-23
Worked Like a champ

Thanks P_Quarles!!!

Holzster


> **p_quarles said:**
> Miro is buggy under Ubuntu. I got it working a lot better, though, by editing the file
/usr/share/python-support/miro/miro/frontend_implementation/VideoDisplay.py

Uncomment the line that says```
self.add_renderer("gstrenderer")
```
And then comment out the line that says```
self.add_renderer("xinerenderer")
```
And, obviously, if you aren't sure how to do this, just ask.

---

### Post by benx009 on 2007-07-23
> **quicksilver1024 said:**
> Hi,

I have been neglecting my problem with Democracy Player for quite some time now, but now I want to finally fix it!
After a few seconds of launching the program, it closes itself and gives the following error:

WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
TIMING   gtkAsyncMethod: <function _gtkInit at 0x8a9b4c4> took too long: 5.352
alsa
oss
pulseaudio
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a345dc> took too long: 4.381
TIMING   gtkSyncMethod: <function getDisplay at 0x8a9b6bc> took too long: 4.423
INFO     got file:///tmp/tmpJiCVVM.html
TIMING   Icon clear: 9.504
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (34.613 secs)
TIMING   idle (Finishing startup) cumulative is too slow (34.613 secs)
TIMING   gtkAsyncMethod: <function selectDisplay at 0x8a9b64c> took too long: 9.532
INFO     got file:///tmp/tmp3-sCz1.html
TIMING   timeout (Feed update (Feedless Videos)) too slow (0.609 secs)
TIMING   gtkAsyncMethod: <function fillMovieData at 0x8a3464c> took too long: 1.456
TIMING   timeout (Save database) too slow (3.472 secs)
TIMING   gtkAsyncMethod: <function fillMovieData at 0x8a3464c> took too long: 1.162
INFO     *** Daemon ready ***
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
TIMING   WARNING: Calling <bound method HTTPDownloader.onHeadersRestart of <dl_daemon.download.HTTPDownloader instance at 0x82e746c>> on HTTPClient: [http://www.ragtagfilms.net/wngpodcast/morningafter.mp4](http://www.ragtagfilms.net/wngpodcast/morningafter.mp4) too slow (0.573 secs)
TIMING   gtkAsyncMethod: <function fillMovieData at 0x8a3464c> took too long: 2.826
TIMING   WARNING: Calling <function <lambda> at 0x9da4d14> on HTTPClient: [http://youtube.com/img/pic_youtubelogo_123x63.gif](http://youtube.com/img/pic_youtubelogo_123x63.gif) too slow (5.794 secs)
TIMING   idle (Start Downloads) too slow (0.521 secs)
TIMING   timeout (Save database) too slow (1.428 secs)
TIMING   WARNING: Calling <function <lambda> at 0x9da50d4> on HTTPClient: [http://ted.streamguys.net/TEDTalksvideo_tile.jpg](http://ted.streamguys.net/TEDTalksvideo_tile.jpg) too slow (0.960 secs)
TIMING   feed update for: [http://feeds.feedburner.com/comedycentral/motherload](http://feeds.feedburner.com/comedycentral/motherload) too slow (0.436 secs)
TIMING   feed update for: [http://abcnews.go.com/xmldata/xmlPodcast?id=1478958&src=i](http://abcnews.go.com/xmldata/xmlPodcast?id=1478958&src=i) too slow (0.136 secs)
TIMING   WARNING: Calling <function <lambda> at 0x9da51b4> on HTTPClient: [http://podcast.msnbc.com/audio/podcast/images/pdv_nn_netcast.jpg](http://podcast.msnbc.com/audio/podcast/images/pdv_nn_netcast.jpg) too slow (1.926 secs)
TIMING   feed update for: [http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml](http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml) too slow (0.520 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - [http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml](http://www.adultswim.com/williams/podcast/tools/xml/video_rss.xml))) too slow (0.625 secs)
TIMING   feed update for: [http://www.discovery.com/radio/xml/sciencevideo.xml](http://www.discovery.com/radio/xml/sciencevideo.xml) too slow (0.425 secs)
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

I uninstalled Democracy player to install Miro (the 'newer' DP) to see if it would fix my problem, but it didn't.

Any help is appreciated thanks.

looks like you may also be having a java problem.  do you have java installed (and working as it should)?.  if you don't, install/reinstall the **sun-java6-bin** package from the ubuntu repos

---

### Post by benx009 on 2007-07-23
also install the **sun-java6-plugin** package just to be safe:)

---

### Post by quicksilver1024 on 2007-07-26
Java is working for sure since I am running Azureus. Although, I had to update it since Azureus crashed a few weeks before. 

All three methods mentioned did not work.

This includes, Java, updating and upgrading files and changing the config file.

Any ideas?

---

### Post by ConfidentiaL on 2007-07-31
I had the exact same problem as you, but I now got it working. What I found out was, that my .miro folder and all subfolders and files were actually owned by root. A quick permission editing using "sudo nautilus" got my permissions back, and miro was working. I also had a problem that it crashed after a few seconds after the gui was up, but it was just a matter of selecting an other tab than "Miro Guide" as soon as miro opened.

Hope this helps :)

---

### Post by quicksilver1024 on 2007-08-04
Nope. The owner is set to the user and not root.
Sigh...I want to watch my podcasts. :(

---

### Post by GrimJack on 2007-08-10
I'm having the same issue with Miro after moving to Compiz-Fusion.

When launched, Miro closes while the Miro Guide is loading. If I quickly click (select) another category or feed before the Guide crashes the program, then it continues to run OK and I can view any of my feeds. But if I select the Guide at any time, it immediately crashes / exits.

Anyone have any idea why this is happening and what can be done to fix it? I'm new to Miro and miss being able to browse and subscribe to new feeds.

TIA

---

### Post by quicksilver1024 on 2007-09-07
FINALLY!

Problem solved - I simply deleted my .miro folder located in my Home folder. To see the folder, go to View Hidden Files.

---

### Post by tvor on 2007-10-29
It's still shutting down after few seconds.
Also, how do you update python libraries without upgrading to Gusty? Thanx

```
pajda@pajda-laptop:~$ sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libxine-extracodecs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.4kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Get:1 http://cn.archive.ubuntu.com feisty/multiverse libxine-extracodecs 1.1.4-2ubuntu3 [39.4kB]
Fetched 39.4kB in 0s (55.5kB/s)             
Selecting previously deselected package libxine-extracodecs.
(Reading database ... 118310 files and directories currently installed.)
Unpacking libxine-extracodecs (from .../libxine-extracodecs_1.1.4-2ubuntu3_all.deb) ...
Setting up libxine-extracodecs (1.1.4-2ubuntu3) ...
pajda@pajda-laptop:~$ miro
/usr/bin/miro.real:84: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

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
INFO     Starting up Miro
INFO     Version:    0.9.9.1
INFO     Revision:   unknown
INFO     Builder:    ben@pitpat
INFO     Build Time: 1189015412.11
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/pajda/.miro/sqlitedb
TIMING   Database load slow: 0.184
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
alsa
oss
pulseaudio
arts
esd
file
none
INFO     loaded renderer 'xinerenderer'
INFO     got file:///tmp/tmpICejfF.html
TIMING   Icon clear: 0.404
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.622 secs)
INFO     got file:///tmp/tmpIo4on_.html
INFO     got https://www.miroguide.com/
TIMING   timeout (Feed update (Feedless Videos)) too slow (1.031 secs)
INFO     *** Daemon ready ***
Segmentation fault (core dumped)
pajda@pajda-laptop:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
pajda@pajda-laptop:~$ 


```

---

### Post by onetb on 2007-11-11
Worked for me p_quarles.  Merci!

---

### Post by Louis Cypher on 2007-11-19
This worked for me on version 1.0  Thx

---

### Post by asphixmx on 2007-11-27
Thanks a lot p_quarles!!! Miro, with compiz effects enabled, always crashed if a pressed PLAY to any video. I had to disable compiz fusion effects to PLAY videos correctly. Now, with your great tip, I fixed it. I can play videos now without touching my compiz fussion effects.

---

