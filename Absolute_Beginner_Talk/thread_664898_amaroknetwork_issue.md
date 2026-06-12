---
title: "amarok\network issue"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-11
Hello,
I am trying to use amarok to play some music on a network share.  The network share is a windows xp box, and when I click to play the file I get the following error.

[B]No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
smb://okit6831pc/Share/Music/JR-Music/03 Walk.mp3[/B]

can I fix this and how?

Thanks
Kezz

---

### Post by Arthur Archnix on 2008-01-11
Can you play local mp3 files? If so then we're looking at a network issue. If not a simple command should fix it:
```
sudo apt-get install ubuntu-restricted-extras
```
This adds lots of stuff, like java, flash, microsoft core fonts. If you just want to install mp3 playback I believe you need to install the ugly pack of gstreamer stuff.
```
sudo apt-get install gstreamer0.10-plugins-ugly
```
If you get an error then you may not have the universe/multiverse repositories enabled. We'll cross that bridge if we have to.

---

### Post by KezzerDrix on 2008-01-11
yes, sorry, I was in a hurry earlier.

I can play local .mp3's and I can play the networked .mp3's using gnomes player rythem box.  

I want to use Amarok simply because I like it better.  I am a computer specialist for a corporation and I have set up an "under the table" media server.  It is constantly changing which makes it fun to listen to, I could just use gnomes player but to be honest I will probably switch to KDE and will need to have amarok working.

---

### Post by Arthur Archnix on 2008-01-12
Ah.. I understand. I'm not much of a network guy, but you might start your search for a solution here:

[http://amarok.kde.org/wiki/Samba](http://amarok.kde.org/wiki/Samba)

Here's a fellow with a similar problem, and some helpful amarokians have suggested some solutions:

[http://amarok.kde.org/forum/index.php/topic,13485.0.html](http://amarok.kde.org/forum/index.php/topic,13485.0.html)

Best of luck,

---

