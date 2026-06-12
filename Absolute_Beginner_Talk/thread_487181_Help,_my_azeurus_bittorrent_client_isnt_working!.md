---
title: "Help, my azeurus bittorrent client isnt working!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by rodami on 2007-06-28
I was downloading some stuff the other day, so I turn on my computer, surf a while and start Azeurus to keep downloading, and it starts up fine, stays there for like 5 secs, and then shuts down by itself, wtf? Why could this happen?

---

### Post by Rocket2DMn on 2007-06-28
People seem to have a fair number of problems like this.  A good fix seems to be deleting the logs.  Change to your home directory, do CTRL+H to show hidden files, and change to the .azureus directory.  Delete logs and restart azureus.
If the problem persists, run azureus from terminal by just typing "azureus" and show us the output.

---

### Post by rodami on 2007-06-28
david@david-laptop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Thu Jun 28 18:26:20 EST 2007::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::516:
  Inconsistent stream length for 'http://192.168.1.1:2869/IGatewayDeviceDescDoc': expected = 3443, actual = 3444
    ResourceDownloaderURLImpl$2::runSupport::319,AEThread::run::69
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=7658, tid=3084703424
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid7658.log
DEBUG::Thu Jun 28 18:26:21 EST 2007::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::516:
  Inconsistent stream length for 'http://192.168.1.1:2869/WanIPConnectionDescDoc': expected = 13757, actual = 13758
    ResourceDownloaderURLImpl$2::runSupport::319,AEThread::run::69
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
david@david-laptop:~$

---

### Post by Rocket2DMn on 2007-06-28
There are a bunch of other posts on such problems, like:
[http://ubuntuforums.org/showthread.php?t=353197](http://ubuntuforums.org/showthread.php?t=353197)
[http://ubuntuforums.org/showthread.php?t=487049](http://ubuntuforums.org/showthread.php?t=487049)
[http://ubuntuforums.org/showthread.php?t=453720](http://ubuntuforums.org/showthread.php?t=453720)
that "jar" file solution also seems to fix problems.  I haven't seen that stream length error before, though.
If you run a search through the forums for "azureus" you will get a million hits.

---

### Post by jackmc on 2007-06-28
The jar solution is a more permenant fix then the logs, do that.

---

