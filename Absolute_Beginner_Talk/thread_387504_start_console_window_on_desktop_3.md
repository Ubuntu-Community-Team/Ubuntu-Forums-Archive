---
title: "start console window on desktop 3"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by xpan on 2007-03-18
Is there any way I can start (automatically) a console window at desktop 3 every time I log into ubuntu?

---

### Post by CSandman on 2007-03-20
in System=>Preferences=>Sessions you can choose what you want to start at the beginning of each session and about having it start on desktop three...  I'm not too sure about how to tie an app to a preferred workspace yet.  I'll look into it!

---

### Post by CSandman on 2007-03-20
Back again with a solution for assigning an app to a workspace, it isn't something that gnome itself supports but with devil's pie it looks like you can do all that and then some.  I personally haven't tried devil's pie but I think I may have to give it a try!
You can get the tarball and additional info here:
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

cheers!

---

### Post by freakavoid on 2007-04-14
I just stumbled upon this thread. 

```
 gnome-terminal -x wmctrl -r Gnome-terminal -t 3 -x
```

might work if somebody still cares :)

---

### Post by xpan on 2007-04-14
i still care... thanks :)

---

### Post by freakavoid on 2007-04-14
Well, I just tried it and it doesn't do the job. But this does:

```

#!/bin/bash 
gnome-terminal&
sleep 1s;
wmctrl -r Gnome-terminal -t 3 -x;

```

Place it into a file, make it executable and add it to the startup programs.

---

