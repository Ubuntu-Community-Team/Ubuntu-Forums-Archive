---
title: "Getting AAC and library to work in Amarok"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Wormsie on 2006-08-18
I got myself a new iPod, and would like to use it under Linux (yes, I am a masochist). Although gtkpod works, I'd like to try other alternatives (as I find gtkpod a bit clumsy), so I decided to give Amarok a try.

I've used Amarok before, and even back then I had problems with AAC playback and adding AAC files to my library. If I use the arts engine, Amarok won't play AAC files or add them to the Library. If I use xine, Amarok will play AAC but still won't add those files to my library. Ogg and mp3 work, though. Any advice?

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
I don't like amaroK, it kept crashing all the time when playing my music.

Why don't you try [Quod Libet](http://www.sacredchao.net/quodlibet/)? It's a GTK+ application, so it will integrate nicely into the GNOME environment, and it uses GStreamer for audio playback! Should play AAC with no problem if you have the GStreamer faad decoder installed. Quod Libet also has a pretty cool [iPod plugin](http://www.sacredchao.net/quodlibet/wiki/Plugins/iPod), but it won't run on Dapper's old version, so one has to wait until edgy or install Quod from source to be able to use newer plugins like that one.

---

### Post by Wormsie on 2006-08-18
Yep, Quod Libet is on my to-try -list. Amarok works for me (although it is resource heavy), but I'd like to have a consistent Gnomeish -look.

I have never ever compiled anything from source, but it can't be that bad. Thanks for the encouraging suggestion. :)

EDIT: However, I'd like the iPod support to be as good as possible, so Quod Libed might not be for me in that sense.

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
You don't need to compile Quod Libet, as it's a Python application!

You do need to compile the tray icon and support for multimedia keys, though, and I keep getting errors, so that might be a bit difficult. :/

To install Quod Libet from source, all you need to do is type sudo make install. You can also run it from the directory you unpacked the archive into, by typing in *./quodlibet.py*, but I don't know if it'll load plugins then. Perhaps?

I'd like to be able to use the new plugins, so maybe I should make a deb package of the most recent version... or on the other hand, maybe not.

The iPod plugin's website states what features are supported, and which aren't. I mainly love Quod Libet for it's simplicity and awesome tagging features, which kinda reminds me of foobar2000! When I get an iPod, I'm gonna install Rockbox anyway, so iPod integration ain't all that important for me. :P

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
Wait, I think python-dev and swig were the packages I was missing to compile the extensions. Now the compile ran just fine! Quod Libet and its plugins can be ran from any directory, so just replace ~/.quodlibet/plugins/songsmenu in the iPod plugin installation guide with /plugins/songsmenu in the directory you unpacked Quod Libet to. I don't have an iPod here, so I can't try it, but the plugin does show up, and seems to work.

---

### Post by hugmenot on 2006-08-18
You can save the hassle and use the packages prepared by **mlind**

[http://www.ubuntuforums.org/showpost.php?p=1240418&postcount=69](http://www.ubuntuforums.org/showpost.php?p=1240418&postcount=69)

---

### Post by Wormsie on 2006-08-18
> **&#12465 said:**
> When I get an iPod, I'm gonna install Rockbox anyway, so iPod integration ain't all that important for me. :PWhoa, I thought the only iPod firmware replacement was Linux for iPod which doesn't really work. I have to look into Rockbox! ;)

---

### Post by Wormsie on 2006-08-18
> **hugmenot said:**
> You can save the hassle and use the packages prepared by **mlind**

[http://www.ubuntuforums.org/showpost.php?p=1240418&postcount=69](http://www.ubuntuforums.org/showpost.php?p=1240418&postcount=69)

Sorry:

[http://www.elisanet.fi/mlind/ubuntu/dists/dapper/testing/binary-i386/Packages.gz:](http://www.elisanet.fi/mlind/ubuntu/dists/dapper/testing/binary-i386/Packages.gz:) 404 Not Found

---

### Post by hugmenot on 2006-08-18
Sorry, was sloppy looking up the source. Use this one
[http://www.ubuntuforums.org/showpost.php?p=1268977&postcount=75](http://www.ubuntuforums.org/showpost.php?p=1268977&postcount=75)

---

### Post by gils0040 on 2006-08-18
make sure that you have universe and multiverse repositories enabled and do
"sudo apt-get install libxine-extracodecs" that shouls allow amarok to play your mp3 and aac files.

---

### Post by Wormsie on 2006-08-19
"libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

So no problem there, as I imagined.

---

### Post by Wormsie on 2006-08-19
Now Quod Libet seems to work! The last time I tried it, it didn't show any files in my library...

---

### Post by Wormsie on 2006-09-16
Since Amarok was updated in the repos, it has now started to recognize my AAC files as well.

---

