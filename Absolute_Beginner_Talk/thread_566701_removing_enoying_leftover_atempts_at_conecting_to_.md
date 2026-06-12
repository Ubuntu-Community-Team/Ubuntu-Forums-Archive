---
title: "removing enoying leftover atempts at conecting to server"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by theredfox on 2007-10-03
Good evening, (a late one it may be) 

I have tried to connect to a friend's ftp server and just screwed up something simple. No big deal, but now I have these icons on my desktop that are folders named as the "name to use for connection" that I gave when trying (and failing) to connect to the ftp server. I can not delete them. they are located in network:///, and from my file browser while in network:/// I try to move them to the trash, and it says they will just be deleted, which is the objective here... so that would be fine, however,  I get an error that says "operation not permitted". 

This seems like one of those - so simple I'm going to be embarrassed - things... 

Please help me remove these files... 

Cheers!

---

### Post by jfinkels on 2007-10-04
Can you right click on them and try to "Disconnect" or something like that?

If you can't figure out how to disconnect, you can hide network volume icons by using 'gconf-editor'. Open gconf-editor by typing <Alt>+<F2>, then typing:```
gconf-editor
```

Descend through the hierarchy on the left-hand side to "apps > nautilus > desktop", I believe. Now on the right hand side you should be able to choose what is visible on the desktop.

---

