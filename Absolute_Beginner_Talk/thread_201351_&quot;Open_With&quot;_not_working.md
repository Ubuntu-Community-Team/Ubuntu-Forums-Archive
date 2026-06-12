---
title: "&quot;Open With&quot; not working"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by kzip on 2006-06-21
I have a fresh install of Dapper and I wanted to change the default movie player. I right click on the movie, choose "Properties" and goto the "Open With" tab (so far so good).. there are three entries and one of the unselected is "Mplayer Movie Player" (the one I want to use) but I cannot select it, or for that matter select any of the other choices. It simply won't change the selection.

I thought this might just be a problem isolated to the movie players - but I tried to do the same on an image file and had the same issue - I just can't change the application.

Any clues? :confused:

---

### Post by ProjectGod on 2006-06-22
i believe there is a GUI tool to set application defaults. so that file extensions are opened by specified programs... da da di ta ta dum?

---

### Post by Blitzace on 2006-06-22
You mean "set preferred applications?" I dont think that works for anything other than default internet browser and default email program... I might be wrong..

I'm sorry this is a stupid question kzip but are you clicking on the black circle? I think you actually need to click there.. Otherwise I'm stumped. I guess if worst comes to worst you will need to set your preffered application in the Gnome Configurator which isn't too hard. (I'm not on ubuntu now though so I can't tell you where to look in the configurator sorry.)

---

### Post by aysiu on 2006-06-23
Maybe you don't have access to something in your own home folder? ```
sudo chown -R kzip:kzip /home/kzip
``` will give you ownership to all your folders and files. Please be very careful using this command and don't use it on any other directories--only your home folder!

---

### Post by kzip on 2006-06-25
[QUOTE=aysiu]Maybe you don't have access to something in your own home folder? ```
sudo chown -R kzip:kzip /home/kzip
``` will give you ownership to all your folders and files. Please be very careful using this command and don't use it on any other directories--only your home folder![/QUOTE]

Beautiful! Worked a treat, thanks a lot! 

One question though would be why did this happen? It was a fresh install of Dapper and I hadn't messed around with permissions etc.

Anyway, that got it working so thanks again :)

---

### Post by aysiu on 2006-06-25
This may explain it--it's the only way I know of personal configuration files accidentally becoming owned by root:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by kzip on 2006-06-26
Ok that makes sense, I probably did run sudo on some graphical applications (though I can't say which) while following some guides on here. Thanks for the link, some interesting info and I'll try and remember to use gksudo for non-command line apps in future :)

---

