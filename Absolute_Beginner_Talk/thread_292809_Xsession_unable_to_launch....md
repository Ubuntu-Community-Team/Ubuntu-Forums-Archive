---
title: "Xsession: unable to launch..."
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by yaauu on 2006-11-04
Hi!

I'm running compiz on top of Xgl in a Ubuntu Edgy, with fglrx drivers.

In /usr/share/xsessions/xgl.desktop I have:
```

[Desktop Entry]  
Encoding=UTF-8 
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/local/bin/startxgl.sh 
Icon= 
Type=Application 

```

And in /usr/local/bin/startxgl.sh I have:
```

#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & 
DISPLAY=:1 
exec gnome-session

```

Ok, the problem is that when I log in selecting "xgl", an error is raised, saying something like: 
```

Xsession: unable to launch /usr/local/bin/startxgl.sh. X session not found, falling back to default session

```
and /usr/bin/startxgl.sh exists. When I press "ok", it loads Xgl and compiz correctly (I can use the compiz effects), but without the usual edgy theme (different icons, the top of the windows is blue instead of orange, etc.).

I have no clue about how to fix this. Can anybody help me? Thank you so much in advance.

---

### Post by Ecthelion on 2006-11-04
Not really a fix but... did you try Beryl?

There are great HOWTO's and... well it's great.
I had xgl-compiz before but I also had problems...

Beryl ROCKS \\:D/

---

