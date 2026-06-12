---
title: "Get rid of rogue app right-click option?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-16
I downloaded and attempted to install a program called 'Alarm Clock'. When I ran the install there was some .so file it couldn't find.

I wasn't too worried about it, deleted the folder it had unzipped to, and forgot about it.

But now whenever I right-click on anything one of my options is "Open with Alarm Clock" - how can I get rid of this option, since the application no longer exists anywhere on my system?

Also if anyone has any personal recommendations for alarm-clock type apps I'd appreciate those. I don't care about a widget-style clock; I just want the ability to set pop-up/audio alarms easily.

Thanks.

---

### Post by RIchard James13 on 2008-01-20
[http://ubuntuforums.org/archive/index.php/t-507360.html]("http://ubuntuforums.org/archive/index.php/t-507360.html")

First things look in your ~/.gnome2/nautilus-scripts folder for a script that might be doing this. 
Go Places->Home Folder
Press CTRL-H to view hidden files and folders
find the .gnome folder and enter it
find the nautilus-scripts folder and enter it
there might be script in there normally that folder is empty

If you can't find it read the thread I posted a link to and try some of the techniques in there. They are trying to add things to that menu, you want to remove it.

---

### Post by blueridgedog on 2008-01-20
I was going to suggest that as well, but the OP did not mention that it was buried under "Scripts" on the menu tree.  I have been watching the thread to see if a simple explanation of managing context menus would appear.

---

### Post by blueridgedog on 2008-01-20
Perhaps the application installed nautilus-actions.

Do you get anything when you run:

```
 nautilus-actions-config
```

---

### Post by jjsonp on 2008-01-21
Thanks for the tips.

However, the only thing in my Nautilus Scripts folder is an 'Open Text Editor Here' script.

Also, when I run 'nautilus-actions-config' I get a 'not currently installed' message, and directions for downloading/installing it.

---

### Post by RIchard James13 on 2008-01-21
> **jjsonp said:**
> Thanks for the tips.

However, the only thing in my Nautilus Scripts folder is an 'Open Text Editor Here' script.

That doesn't sound like it

> 
Also, when I run 'nautilus-actions-config' I get a 'not currently installed' message, and directions for downloading/installing it.

It is not installed by default. I suggest you install it just to see if something is hiding in there.

---

### Post by RIchard James13 on 2008-01-21
Also if you can't find anything with that try running it as the super user with the sudo command.

---

