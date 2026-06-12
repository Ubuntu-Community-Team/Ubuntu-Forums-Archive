---
title: "How do i watch videos on this site?"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by dbzsongoku on 2005-11-11
Hi,
I'm a noob ubuntu user that has a problem trying to watch streaming videos from [www.aznv.tv](www.aznv.tv).  Under windows I would just use winamp 5 to stream the videos and they would play fine.  But I don't think there is winamp 5 on linux so i don't know what software to use.  Any help would be great.
Thanks

---

### Post by apjone on 2005-11-11
mplayer with mplayer-mozilla plugin

---

### Post by Third Thoughts on 2005-11-11
[QUOTE=apjone]mplayer with mplayer-mozilla plugin[/QUOTE]

If you need a how to on how to install it and get it working look here  [http://ubuntuforums.org/showthread.php?t=75817](http://ubuntuforums.org/showthread.php?t=75817)
The how to is missing on step though. You need to go into the /usr/lib/mozilla-firefox/plugins and delete the totem plugins. If you don't konw which plugins those are there is an easy way to find out. Go to the location bar in mozilla and type in "about:Plugins" (no www or anything like)  You'll get a page displaying all the plugins firefox is using. Scroll down until you see the info on the totem plugins. One of the things is will tell you is the plugin file. Just go and delete it (you'll have to be root) and then the mplayer plugin should be your default internet player.

~Andrew S.

---

