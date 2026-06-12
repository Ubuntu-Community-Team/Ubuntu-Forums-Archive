---
title: "No Sound with Flash/Firefox"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by lilr0x on 2006-08-04
I can't seem to get sound with firefox and flash for things like pandora.com, video.google.com and youtube, etc.

Is this common or easy to fix?
I've update firefox and ubuntu as much as possible with the update manager, synaptic and easyubuntu.

Thanks.

---

### Post by BitTorrentBuddha on 2006-08-04
```
sudo apt-get install alsa-oss
```Then each time you run firefox make sure it's run as ```
aoss firefox
``` instead of just firefox, so remember to change your panel launchers, menu entries, and any other things you use to start firefox.

---

### Post by dr k on 2006-08-04
install:

libflash-mozplugin

and you should be right.

---

