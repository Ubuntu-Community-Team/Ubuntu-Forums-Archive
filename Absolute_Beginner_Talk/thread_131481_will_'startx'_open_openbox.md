---
title: "will 'startx' open openbox?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-16
if the only wm i have is openbox, then i guess i don't need wdm. so, if i just enter 'startx' in the terminal, will it open openbox, or do i have to edit something before that will happen? hope you're having a lovely day.

---

### Post by WolfJay_83 on 2006-02-16
You may need a file telling the server which wm to start.

if you create a file .xinitrc that looks like
```

#!/usr/bin/env bash
exec openbox

```

sometimes the file needs to be called .xsession instead. This has something to do with display managers being installed- if one doesnt work, just rename the file.

If you apt-get install xdm, gdm, or kdm, you wont need to create this script as the display manager will allow you to select any installed window managers.

---

### Post by fuscia on 2006-02-16
what i meant was if openbox is the *only* wm i have, will 'startx' bring up openbox by default, or do i need to do something? (i want to get rid of the dm if i don't need it.)

---

### Post by johnraff on 2006-02-21
According to this guy you can start up with "startx" without a dm.
[http://ubuntuforums.org/showthread.php?t=62650&highlight=HOWTO%3A+openbox](http://ubuntuforums.org/showthread.php?t=62650&highlight=HOWTO%3A+openbox)

---

### Post by abhaysahai on 2006-02-22
you definately do not need a DM to startx, only xorg is required. 
and ofcourse configured too. 
xorg has a default DM inbuilt in it -- I don't remember the name, but it comes up if you do not specify any DM. 

for starting openbox the .xsession idea is the best.

---

