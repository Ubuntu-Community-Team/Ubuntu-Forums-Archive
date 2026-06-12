---
title: "a few questions about transset..."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-23
ok, i know how to use the transset, but i need to know how to change the text color of the text in xterm to white, so it shows up on my black desktop.  How would I do this?

btw, is there any way to make all xterm use my transset instead of typing transset in the terminal everytime i start up xterm...like have it default to the setting?

---

### Post by 23meg on 2006-12-23
> 
ok, i know how to use the transset, but i need to know how to change the text color of the text in xterm to white, so it shows up on my black desktop. How would I do this?
Add
```
xterm*foreground: white
```
to your ~/.Xdefaults file, and start xterm with```
xterm -tn xterm-color
```
> 
btw, is there any way to make all xterm use my transset instead of typing transset in the terminal everytime i start up xterm...like have it default to the setting?

You can use [transset-df]("http://forchheimer.se/transset-df/") to do that.

---

### Post by zetsumei on 2006-12-23
i guess what im trying to ask is how do i get my terminal fully transparent but with white text on my black desktop background.  some screenshots i see have just text on the desktop with the cursor.

---

### Post by 23meg on 2006-12-23
See these threads:

[http://www.ubuntuforums.org/showthread.php?t=81727](http://www.ubuntuforums.org/showthread.php?t=81727)
[http://www.ubuntuforums.org/showthread.php?t=202249](http://www.ubuntuforums.org/showthread.php?t=202249)

I've only tried it with gnome-terminal though; the best I know about how it can be done with xterm is in my first post.

---

