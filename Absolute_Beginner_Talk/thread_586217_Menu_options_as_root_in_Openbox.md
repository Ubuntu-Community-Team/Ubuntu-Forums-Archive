---
title: "Menu options as root in Openbox"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-10-22
Hi everyone, before you read on, please do not refer me to obmenu if at all possible.  It's pretty late where I am and I spent quite a bit of time trying to get it configured and ended up with a headache.

I am hand editing the menu xml which has gone error free so if possible I would like to keep doing so.  My problem is that I need certain applications to be run as root like nmap, gedit (when editing /etc/X11/openbox/menu.xml).  How can I edit them into the menu.xml so that they are run as root when clicked off of the menu?  Thanks for the help.:)

---

### Post by TeaSwigger on 2007-10-22
Hello, assuming it is a GUI app, try adding gksu to the command if you are using an ubuntu/gnome or xubuntu/xfce base, or kdesu if you are using kubuntu/kde. For example:

```
gksu gedit /etc/X11/openbox/menu.xml
```

rather than just "gedit /etc/X11/openbox/menu.xml" if you want to run it as root. I use Fluxbox a lot and made my own menu so I empathize. Luck :)

---

### Post by fuscia on 2007-10-22
got your pm. i don't know a whole lot about openbox other than what i've had to learn (though, i did stay at a holiday inn express, last night).

if you're trying to write root opening of gedit, of a particular file, into the menu, i think you need something  like *gksu gedit -e whateverthestupidfileis.txt* (you might also try *%n* or *%f* if *-e* doesn't work. i wouldn't have a clue as to what these do, though. they're tricks i've acquired rather than code i understand). also, why do you need to edit the menu as root? why not just copy it to /home/you/.config/openbox and edit as user?

---

