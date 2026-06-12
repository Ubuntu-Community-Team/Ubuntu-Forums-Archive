---
title: "Deluge Bit Torrent Wont Start Up"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-06-18
I get the folillowing error:

no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted


What does this mean? Deluge was working fine before. I tried removing, purging and re-installing it, but no luck!

---

### Post by BoneyOne on 2007-06-19
It's a known error, but thankfully an easy fix.

Just delete ~/.config/deluge/persistent.state file.

---

