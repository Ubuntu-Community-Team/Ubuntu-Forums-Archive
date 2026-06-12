---
title: "Compiz installed but there is a bug."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-07-15
I followed this (now closed)thread to install Compiz. 

[http://www.ubuntuforums.org/showthread.php?t=133427](http://www.ubuntuforums.org/showthread.php?t=133427)

All seemed well, however when i log into Compiz things run ok for a few minutes and then all of the titlebars disappear. Not sure why they would run for awhile and then quit.

The only fix I have found to bring them back is

```
nohup metacity --replace &
```

However, now logging into Gnome, even fail safe yields no title bars unless I run this funtion. 

Any help on how i can fix this would be appreciated.

---

### Post by Anduu on 2006-07-15
I suspect that one of the compiz plugins is causing problems...might take some trial and error to figure out which ones...

To get title bars back when logging in to regular Gnome all I did was add metacity to my startup list under Preferences>Sessions>Startup Programs

---

