---
title: "Playing MP3's in websites with Foxfire?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Nexusx6 on 2006-08-21
I visit a site pretty frequently that loads a lot of MP3 files for the sound on variouse pages. The problem is, is that Firefox asks for a plugin to play the MP3 files after the page is installed... but when I tell it to search for the plugin, it says there arn't any :sad:

Is there a work around for this? The said site just isn't funny without the goofy sounds/music going on :frown:

---

### Post by Major_Stitch on 2006-08-21
Did you configure Ubuntu to play mp3s? If you didn't, go to [Restricted Formats Wiki Page]("https://help.ubuntu.com/community/RestrictedFormats"). But if you did, did you install the firefox plugin for Totem (or any other player you use) through synaptic? Please check all of this!

---

### Post by Nexusx6 on 2006-08-21
> **Major_Stitch said:**
> Did you configure Ubuntu to play mp3s? If you didn't, go to [Restricted Formats Wiki Page]("https://help.ubuntu.com/community/RestrictedFormats"). But if you did, did you install the firefox plugin for Totem (or any other player you use) through synaptic? Please check all of this!

Yup, Ubuntu plays mp3's just fine, but I didn't know about a Totem plugin for Firfox :eek: Sounds like what I'm missing

---

### Post by Major_Stitch on 2006-08-21
Are you using Totem? Did you install totem-gstreamer or totem-xine? For the first one it's totem-gstreamer-firefox-plugin package and if it's the second one than it's totem-xine-firefox-plugin. Did you install all of the gstreamer plugin packages from [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")?

---

### Post by Nexusx6 on 2006-08-21
I use Kaffeine (I do have Totem though, and all gstream plugins.. only recently switch to KDE), but I used your hint and found the Kaffeine plugin for foxfire (kaffeine-mozilla) and now MP3's play off the site again :D 

Many thanks Major_switch ^(^^)^ I didn't know there were Firefox plugins for a lot of the players in the Repositories.

---

### Post by Major_Stitch on 2006-08-21
No problem, glad to help!

---

### Post by Average Joe on 2006-09-12
Ok, I hope that somebody is still checking this thread, because I am having the same problem: I cannot listen to mp3's on a website with Firefox.

I use Amarok as my default music player (although I have a Gnome desktop), and I could not find any Firefox plugins for that.

Of course, I could use Totem to play the mp3's, but when I try to install the totem-gstreamer-firefox-plugin, I get an error in Synaptic, because this plugin has version 1.4.1-0unbuntu4, while the installed Totem has version 1.4.3-0ubuntu3, and those are not compatible (both are the lastest versions).

OK, then I'll try with xine instead. But when I want to download the totem-xine and the totem-xine-firefox-plugin package, I get the message that totem-gstreamer and *ubuntu-desktop* will be uninstalled. I think I want to keep my ubuntu-desktop though.

I *really* wish simple things like listening to some music on a website were a bit better supported in Ubuntu...

---

