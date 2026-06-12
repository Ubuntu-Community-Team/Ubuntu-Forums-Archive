---
title: "My first applet program thingy..."
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Wangsta on 2006-11-25
I just found out about the 'eject' command and I've decide to use it in my first Linux program or applet or widget or whatever.

Right now, I know **nothing** about programming. I want to make just a extremely simple applet for the Xfce panel. 
I just want a button, that when you click on it, executes the 'eject' command.

How in the world would I figure out how to do this? What makes something qualify as an applet? I have no idea!

---

### Post by WiseElben on 2006-11-25
The easiest way would be to make a script and then making an icon on the panel that runs the script. Here's a sample script:

```

#!/bin/bash
#ejects the cd tray
eject

```

Name this script whatever you want, then put it in a folder, maybe ~/bin/, and then make an icon. In the command, type in "/path/to/script/scriptname"

Without the quotes, of course. There ya go, a simple script that runs off an icon. By the way, you wouldn't call this an applet.

EDIT: Haha.. I just realized that you could just make an icon with "eject" in the command line. So much easier! But at least now you know how to do more complex scripts.

---

### Post by WiseElben on 2006-11-25
> **WiseElben said:**
> The easiest way would be to make a script and then making an icon on the panel that runs the script. Here's a sample script:

```

#!/bin/bash
#ejects the cd tray
eject

```

Name this script whatever you want, then put it in a folder, maybe ~/bin/, and then make an icon. In the command, type in "/path/to/script/scriptname"

Without the quotes, of course. There ya go, a simple script that runs off an icon. By the way, you wouldn't call this an applet.

EDIT: Haha.. I just realized that you could just make an icon with "eject" in the command line. So much easier! But at least now you know how to do more complex scripts.

EDIT 2: I'm not sure how to do it on xfce, but when you right click, the option that should be something like "Custom application launcher." That's what it is on Gnome anyway.

---

### Post by junglepeanut on 2006-11-25
If you are just playing you may not want to put it in bin yet, as you just want to be able to click on it on the desktop and have it work.

So you could do exactly as WiseElben said, except leave the file on the desktop and 

from a terminal

chmod 755 thescriptname

Also I built it in xfce and it is pretty cool. If you want to do like he says and  create a launcher just click on the the taskbar panel and do as he instructed. I think if you are going to create applets the way to start would be 

vim eject #or use gedit etc 

save_that_code_in_this_file

chmod 755 eject

now it is clickable on the desktop

---

### Post by Wangsta on 2006-11-26
> **junglepeanut said:**
> 

Also I built it in xfce and it is pretty cool. If you want to do like he says and  create a launcher just click on the the taskbar panel and do as he instructed. I think if you are going to create applets the way to start would be 

vim eject #or use gedit etc 

save_that_code_in_this_file

chmod 755 eject

now it is clickable on the desktop

Huh? I don't understand what you're saying. Do you mean I should open the script for eject, put it in a new script and change the permissions?

But how does this make it like an applet, such as the 'desktop' button?

---

### Post by junglepeanut on 2006-11-26
Nope, just saying if you make the script, you can put it anywhere if you change the permissions for it to be executable, that way you dont have to fill bin with your testing stuff.

So I made the file. Then I changed the permissions, then I put it on the Desktop (you may not need to do this step). Now it is a clickable script in xfce. In gnome it will ask you do you want to open this or execute. In my xfce settings it knows if its a script and I click on it to execute, whereas I will edit it with vim.

Hope this helps.

---

### Post by kinematic on 2006-11-26
just do this for a simple eject icon/applet/whatever.
right-click in some empty space on our desktop and select "create new starter"
for the command to use select "usr/bin/eject" and select an icon for it.....that's all ;)

---

