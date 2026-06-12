---
title: "problem with Deluge"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-11-28
Hey , I just got Internet installed in my house, and started downloading something with Deluge. It was going fine, then I restarted my computer, and now when I try to use Deluge, it acts as if its about to load but then nothing happens.

edit: the same thing happens when I open Deluge through the applications menu

any idea whats up?

cheers,
kev

---

### Post by corevette on 2007-11-28
what happens when you run 'deluge' in the terminal

---

### Post by shirilover on 2007-11-28
You might trying deleting  ~/.config/deluge/prefs.state and relaunching deluge

---

### Post by Sef on 2007-11-28
Check the [deluge forums]("http://forum.deluge-torrent.org/").

---

### Post by nudnik on 2007-11-28
> **shirilover said:**
> You might trying deleting  ~/.config/deluge/prefs.state and relaunching deluge

I think the above is probably the easiest way to get it working again. Make sure you have the latest build installed, there has been a lot less of that sort of thing (mystery crashes and start errors) with recent builds.

---

### Post by Cochise on 2007-11-28
delete the config file as above then untick the option for UPnP

---

### Post by KevNice on 2007-11-28
ok, i deleted that file, then tried to run it normally, no luck. 
here is what I get when I try to run from terminal:

```
 Traceback (most recent call last):
  File "/usr/bin/deluge", line 136, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 117, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
    common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 276, in __init__
    self.sync(True)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 877, in sync
    self.apply_prefs_per_torrent(unique_ID)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 985, in apply_prefs_per_torrent
    self.get_pref("max_connections_per_torrent"))
  File "/var/lib/python-support/python2.5/deluge/core.py", line 1054, in set_max_connections_per_torrent
    max_connections)
deluge.core.DelugeError: 'No such unique_ID.'
close failed: [Errno 32] Broken pipe

```

looks like something got deleted somehow..

---

### Post by philinux on 2007-11-28
Reinstall it.

---

### Post by KevNice on 2007-11-28
i deleted the config file, and seems to start OK now.

thanks!

---

