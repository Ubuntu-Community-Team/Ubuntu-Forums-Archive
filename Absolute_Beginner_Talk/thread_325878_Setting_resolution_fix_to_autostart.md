---
title: "Setting resolution fix to autostart"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Sasabune on 2006-12-26
I recently got the proper resolution working on my laptop, with the 855resolution utility. I can get the right resolution by running

```
sudo 855resolution 3c 1400 1050
```

and logging out and restarting X (I use KDE). I tried putting the above line (sans sudo) into /etc/X11/xinit/xinitrc , since I figured it would run before X is started. It isn't working though, so what should I do? It seems that it does run at the startup since I just need to restart X to get the proper res.

---

### Post by jive_turkey on 2006-12-26
Check out this thread and see if it helps

[http://www.ubuntuforums.org/showthread.php?t=323636]("http://www.ubuntuforums.org/showthread.php?t=323636")

---

### Post by gborzi on 2006-12-26
I've read that you need to set the card bios before starting X. xinitirc is used while X is starting, not before. One solution is to put a file in /etc/init.d just like 915resolution, see here [http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html). I have found this page that can be useful [http://www.bram.be/travelmate_4651lci.html](http://www.bram.be/travelmate_4651lci.html).
Hope this helps.

---

### Post by Sasabune on 2006-12-26
I put a shell script into /etc/init.d/, but it still wont work. It's not such a big deal since I can just restart X at the login screen, but it would be nice to work automagically.

edit: the shell script doesn't seem be to run at all, even though it's just like others in init.d. WTF?

---

### Post by gborzi on 2006-12-26
Besides putting the script under /etc/init.d, you need to build the "start links" to the rc*.d directories. This can be done using the update-rc.d command > sudo update-rc.d "script name" defaultsI had not mentioned this in my previous post, sorry. In case it still fails, this is possibly due to the fact that the 855resolution script is invoked after the gdm (or kdm, whatever you use) script. In this case look at the update-rc.d manpage to see how to specify the priority.

---

### Post by Sasabune on 2006-12-26
Well that didn't do it either but I stuffed the line into bootmisc.sh and now it works. And I'm content with that O:)

---

