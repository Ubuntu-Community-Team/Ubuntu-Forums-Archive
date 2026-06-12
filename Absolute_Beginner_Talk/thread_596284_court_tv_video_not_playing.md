---
title: "court tv video not playing"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-10-29
Hi , On [http://www.courttv.com/trials/index.html](http://www.courttv.com/trials/index.html)  & [http://crazyshit.com/](http://crazyshit.com/)  I can not play videos
I followed this [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)   Enabling Multimedia in Feisty . when I     go to"Ubuntu restricted extras" in add/remove & try to add them I get error
(screenshot) On the web sites when I try I get them to play I get (screenshot) asking for plugins 
when I click on it I get (screenshot) no suitable plugins were found

To get rid of erroe I do this sudo aptitude purge msttcorefonts

---

### Post by damotor on 2007-11-02
just sudo apt-get install mozilla-plugin-vlc totem-mozilla mozilla-mplayer and one of these players will play the stream

---

### Post by Xbehave on 2007-11-02
it looks lik the problem could be missing repositories. do you have universe and multiverse repos enabled?

---

