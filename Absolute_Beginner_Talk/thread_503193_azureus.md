---
title: "azureus"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-07-17
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb054d172, pid=7096, tid=3085104832
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid7096.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by tcoffeep on 2007-07-18
Stop using that and use (1) {if you're using GNOME} Deluge Torrent or (2) {if you're using KDE} Ktorrent.

Both rock, but I prefer Deluge.

---

### Post by rahul.gupta on 2007-07-18
the same kinda issue occurs for me, the work around i follow is to delete the .azureus folder in my home directory, but remember that this would also remove any torrents that you had queued up to be downloaded. (any downloads in progress can be resumed simply by adding the torrents again, and specifying the same download location)

---

### Post by auraithx on 2007-07-18
> **tcoffeep said:**
> Stop using that and use (1) {if you're using GNOME} Deluge Torrent or (2) {if you're using KDE} Ktorrent.

Both rock, but I prefer Deluge.

Deluge has the same sort of problems.
```
glasgowm@glasgowm-desktop:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Starting DHT...
/var/lib/python-support/python2.5/deluge/core.py:713: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Raising error: 
Error: ''
Traceback (most recent call last):
  File "/usr/bin/deluge", line 83, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 57, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 47, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 217, in __init__
    self.sync()
  File "/var/lib/python-support/python2.5/deluge/core.py", line 638, in sync
    raise e
deluge.core.InvalidTorrentError: ''

```

---

### Post by tcoffeep on 2007-07-18
Could it be a python error?

Do you have the latest version of python?

---

### Post by RomeReactor on 2007-07-18
Hi. I've found that installing **azureus-gcj** helps with Azureus crashes. Also:

> **rahul.gupta said:**
> the same kinda issue occurs for me, the work around i follow is to delete the .azureus folder in my home directory, but remember that this would also remove any torrents that you had queued up to be downloaded. (any downloads in progress can be resumed simply by adding the torrents again, and specifying the same download location)

There's no need to delete the **.azureus** folder; just go into **.azureus/logs** and delete the files there before starting Azureus again.

That said, I really recommend **not** installing the version from the repositories (2.5.0.0) and instead download the version from [their site]("http://azureus.sourceforge.net/") (2.5.0.4); it's much more stable.

---

### Post by auraithx on 2007-07-19
> **RomeReactor said:**
> Hi. I've found that installing **azureus-gcj** helps with Azureus crashes. Also:



There's no need to delete the **.azureus** folder; just go into **.azureus/logs** and delete the files there before starting Azureus again.

That said, I really recommend **not** installing the version from the repositories (2.5.0.0) and instead download the version from [their site]("http://azureus.sourceforge.net/") (2.5.0.4); it's much more stable.

Thank you - Downloading the one from their site was much much more stable! It even gave me an error on start up (good thing) saying it wasn't shut down properly. Which was pretty much the reason it kept crashing.

---

