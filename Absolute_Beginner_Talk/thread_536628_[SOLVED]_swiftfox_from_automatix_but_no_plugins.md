---
title: "[SOLVED] swiftfox from automatix but no plugins"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-08-27
Hello:

I have ubuntu 7.0.4. I installed swiftfox from automatix, but can't get any of my firefox plugins to work (flashplayer, java, totem). Does anyone know the sudo code for this.

I tried a couple of methods I found on the forums.

cd ~/swiftfox/plugins
ls
sudo ln -s /usr/lib/firefox/plugins* .
ls

and

cd /opt/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/*

But neither one worked. Any help would be appreciated.

---

### Post by aysiu on 2007-08-27
Try **copying** and **pasting** these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd /opt/swiftfox
sudo mv plugins plugins.old
sudo ln -s /usr/lib/firefox/plugins /opt/swiftfox/plugins
```

---

### Post by orwellus on 2007-08-28
Awesome. That worked. Thank you.

---

