---
title: "flash sound problem"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by demonoid on 2006-09-15
When I'm with firefox and trying to watch some flash clip from youtube - often there is no sound , because before 3 min i have been listed or watch music or movie with XMMS/Mplayer. How can i configure the flash player or the others programs to haven't sound fight
p.s : srry for the bad english

---

### Post by xyz on 2006-09-15
Hello **demonoid**,
I think I understood you correctly...you need _flash_player_7_linux ?
Some nice people talk and explain here: (don't forget universe/multiverse repositories)
[http://www.ubuntuforums.org/showthread.php?t=257206](http://www.ubuntuforums.org/showthread.php?t=257206)

Don't hesitate to come back and ask questions if it's not clear,
Good luck.

---

### Post by demonoid on 2006-09-15
10x :}

---

### Post by 3rdalbum on 2006-09-15
I think demonoid already has Flash Player, he's just having the same problems with sound that plague us all.

I've not tried this myself, demonoid, but this might help you.

First, download the esound-clients package (go to a terminal and type "sudo apt-get install esound-clients").

Close Firefox. Press Alt-F2 and type "esddsp firefox", and press Okay.

Now, hopefully, this should fix the problem, as long as you launch Firefox in this way.

---

