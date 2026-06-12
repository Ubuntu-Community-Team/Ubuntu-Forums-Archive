---
title: "No UI for Ktorrent"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by TurkVU on 2008-02-14
I've been trying both ktorrent and utorrent (through wine) and both were working fine. Then ktorrent had an issue moving a file after it finished dl'ing. I killed the program and rebooted, and now although both programs seem to launch their processes just fine, I can't get the UI for either to show up on my screen. 

Any ideas?

---

### Post by ashmew2 on 2008-02-15
Have you tried removing/reinstalling Ktorrent ? And may i suggest Transmission (its a torrent client) which i feel is far better than the bot h you have mentioned.

---

### Post by hyper_ch on 2008-02-15
if you want a truly lightweight - yet powerful - client, have a look at rTorrent

---

### Post by mbsullivan on 2008-02-15
Hi!

For me, KTorrent starts minimized to the system tray. Make sure that you're not just missing it! If it's not residing in the system tray, then try killing any running instances and starting it again (paste the following into a terminal window):

```
sudo killall -9 -r ktorrent;  ktorrent 1>/dev/null 2>/dev/null &
```

If you're wondering what this code does, it will kill (with a KILL signal [9], not just a TERM signal, which is the default) any processes containing "ktorrent". It will then run ktorrent in the background, ignoring any wordy output (from the standard output stream [1] or standard error stream [2]).

Hope this helps!
Mike

---

### Post by TurkVU on 2008-02-15
Thanks - looks like it was starting minimized to the system tray - which I just found out is called the notification area in gnome and I didn't have on any of my panels (wasn't there by default which is kinda weird). But I got it working now - so thanks!

---

