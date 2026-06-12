---
title: "listening to a radio"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-20
I wanted to listen to an internet radio, namely bbc, but bbc tells me, that there is a plugin missing. I was using firefox, which tried to find an apropriate plugin, but failed. Is there a kind of realplayer or sth. like this for ubuntu? I would prefer though to listen to the radio in a firefox window. Is this possible?

---

### Post by Kapre on 2006-02-20
[QUOTE=gagatz]I wanted to listen to an internet radio, namely bbc, but bbc tells me, that there is a plugin missing. I was using firefox, which tried to find an apropriate plugin, but failed. Is there a kind of realplayer or sth. like this for ubuntu? I would prefer though to listen to the radio in a firefox window. Is this possible?[/QUOTE]

gagatz - What plugin did bbc tells is missing in your ffox? Do you want to try listening to bbc using another browser (say opera or mozilla)? Sorry that I may not have answered yoru question immediately but we need more info.

K

---

### Post by gagatz on 2006-02-20
No, that wouldn't make any difference, if i could listen to it through opera or mozilla, i'd be fine. But anyhow, how could this work?

---

### Post by btdown on 2006-02-20
BBC uses realplayer and/or wmv. Heres a link for install instructions for realplayer 10
 
[https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29#head-cb218245cb84624bd63829d99069a4be5197abbd]("https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29#head-cb218245cb84624bd63829d99069a4be5197abbd")

---

### Post by darkmaze on 2006-02-20
gxine has several bbc presets.

---

### Post by n1gke on 2006-02-20
Hope this helps.

I use Firefox to get to shoutcast.com, and then from their list I choose my station.

By default, Firefox does not bring up my preferred player, which is XMMS.

I had to manually install XMMS when installing the new version Ubuntu Dapper Drake v6.04.

When the system asks which player you want to use, re-direct it to /usr/bin/xmms

I have listened to many stations this way and saved the playlist for each one for future use.

Cheers.... ..

Myrton - N1GKE -

---

### Post by erikpiper on 2006-02-20
n1gke- BBC doesn't work that way, unfortunatlely. Quite annoying. You HAVE to install realplayer for it to work...

---

### Post by jonathansizz on 2006-03-04
I had the same problem - the BBC have their own radio player, which needs Realplayer to be configured correctly. After installing Realplayer, you  need to copy the files nphelix.so and nphelix.xpt from /usr/lib/mozilla/plugins to your .firefox and .mozilla plugins folders in /home/username/.firefox/plugins and /home/username/.mozilla/plugins.

Then you restart firefox and away you go!

---

