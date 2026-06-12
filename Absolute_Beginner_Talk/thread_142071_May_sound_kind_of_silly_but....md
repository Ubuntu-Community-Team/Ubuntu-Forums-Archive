---
title: "May sound kind of silly but..."
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by derekd on 2006-03-09
How do I change the Firefox icon back to the original one? My friend showed me how a long time ago but I cannot remember.

---

### Post by Aine on 2006-03-09
```
 sudo cp /usr/share/pixmaps/firefox.xpm /opt/firefox/chrome/icons/default/default.xpm
```

I think thats what you mean??

---

### Post by derekd on 2006-03-09
Didn't do anything :-?

---

### Post by aysiu on 2006-03-09
[QUOTE=derekd]How do I change the Firefox icon back to the original one? My friend showed me how a long time ago but I cannot remember.[/QUOTE] How did you change it in the first place...? A script? A command?

---

### Post by derekd on 2006-03-09
No I meant instead of the deer park icon it comes with on Ubuntu I want the normal one like this [IMG]http://yubnub.org/images/firefox.gif[/IMG]

---

### Post by BoyOfDestiny on 2006-03-09
[QUOTE=derekd]No I meant instead of the deer park icon it comes with on Ubuntu I want the normal one like this [IMG]http://yubnub.org/images/firefox.gif[/IMG][/QUOTE]

Right click on the launcher (that "earth" icon), choose properties, (click the earth icon in the properties window) navigate to the location of your icon. 

(For some reason it wouldn't let me click the file directly...) If you have trouble, click ok when you've gotten to the folder with your icon. Then click the now empty iconbox (in the properties window), select your logo file. 

I did it right now just fine in Dapper... In breezy I don't think it had issues selecting the file first...

---

### Post by aysiu on 2006-03-09
This worked for me:
[http://ubuntuforums.org/showthread.php?t=34354](http://ubuntuforums.org/showthread.php?t=34354)

---

