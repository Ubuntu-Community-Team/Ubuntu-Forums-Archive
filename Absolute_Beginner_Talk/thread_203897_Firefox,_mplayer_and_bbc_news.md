---
title: "Firefox, mplayer and bbc news"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-26
I tried to watch the video's on bbc news and what happens is that it returns 3 staggered audio streams creatin this wierd echoing effect.

See screenshot:

[[IMG]http://img101.imageshack.us/img101/1696/screenshothttpnewsbbccoukbbcne.th.png[/IMG]](http://img101.imageshack.us/my.php?image=screenshothttpnewsbbccoukbbcne.png)

How can i fix this?

(This was when i selected the "Real Player" option. I tried Windows media and got the vlc "(no picture)" and nothing else.)

---

### Post by dcstar on 2006-06-26
[QUOTE=bohboh]I tried to watch the video's on bbc news and what happens is that it returns 3 staggered audio streams creatin this wierd echoing effect.

See screenshot:

[[IMG]http://img101.imageshack.us/img101/1696/screenshothttpnewsbbccoukbbcne.th.png[/IMG]](http://img101.imageshack.us/my.php?image=screenshothttpnewsbbccoukbbcne.png)

How can i fix this?

(This was when i selected the "Real Player" option. I tried Windows media and got the vlc "(no picture)" and nothing else.)[/QUOTE]
You may need the Helix player plug-in installed (which Helix player/Realplayer should put in automagically).

There should be a **nphelix.so** and a **nphelix.xpt** file in your Firefox plugins directory (the BBC videos works fine on my FF with these).

---

### Post by bohboh on 2006-06-26
I have installed Helix and it's still the same. I think this is because of how the plugins are registered.

How do i tell firefox that if i click on real audio/windows media links to load helix plugin?

---

### Post by detectiveinspekta on 2006-07-07
Havning trouble with BBC world as well, same problem as you but mine doesn't show the stop play icons.
You can right click the player and in the options disabiling helix option may work.

---

