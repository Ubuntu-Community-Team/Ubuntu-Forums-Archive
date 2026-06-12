---
title: "a question about packet manager"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by mee.six on 2006-10-08
Is it possible to store packages somewere on my computer (or maybe it's clear to see this place, but I didn't find it..).

here is the situation: my internet connection is rather limeted, so I'd like to save packages for further installations... and to share them with people around.
is it possible?


(sorry if I posted in a wrong subforum, but it looks to me like a totally newbie question)

---

### Post by zappa on 2006-10-08
All packages are stored locally in /var/cache/apt/archives
and stay there as long as you don't sudo apt-get clean them. 
But for later installations you can copy them from there of course ;)

---

### Post by mee.six on 2006-10-08
So, if I give packages to friends, they copy it into cache directory and try to install them with packeges manager, manager won't go to server, but will take  files right from hard drive? :)

---

### Post by zappa on 2006-10-08
possibbly yes, but you must have the most recent version and all dependencies ;)

---

### Post by slimdog360 on 2006-10-08
If your on a lan you might want to have a look at squid to install on the server. ```
sudo apt-get install squid
``` 
[http://www.squid-cache.org/](http://www.squid-cache.org/)

---

