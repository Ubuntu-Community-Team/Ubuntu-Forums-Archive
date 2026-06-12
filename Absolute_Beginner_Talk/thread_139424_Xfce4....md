---
title: "Xfce4..."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-03-04
...the minimalist's approach to Desktop.

However, when I minimize my apps...they simply disappear! 
Where do they go?
How do I adjsut my screen resolution? It can't be done through the Settings/XFCE4 display, nothing loads!
Where did the bottom toolbar go?

So many questions...

---

### Post by Xian on 2006-03-04
[QUOTE=qwazert]However, when I minimize my apps...they simply disappear! 
Where do they go?[/QUOTE]

Are you saying the entire panel disappears??
If not, you probably just need to add the taskbar plugin.

---

### Post by 5-HT on 2006-03-04
Hi, let's run through these here.
Xian was right on with the taskbar, and I'll show you how to get it back, among other things, in this post.

[QUOTE=qwazert]

However, when I minimize my apps...they simply disappear! [/quote]

Have you tried a middle mouse click?
That will show all open windows for all the virtual desktops.
If you don't have a middle mouse button, clicking the left and right buttons simultaneously mimicks a middle click.
[QUOTE=qwazert]
Where do they go? [/quote]
Apart from a middle mouse click, you can also have the XFCE taskbar or iconbox. Both of these will list all current windows open.

For the taskbar, enter:
```
 xftaskbar4 & 
```

For the iconbox, 
```
 xfce4-iconbox & 
```

Play around with them, find out which one you want to use, and then kill off the other one:

```
 killall xftaskbar4 
```
```
 killall xfce4-iconbox 
```

**Make sure you select "save session" when logging out, so that on the next login your changes will be reflected


[QUOTE=qwazert]
How do I adjsut my screen resolution? It can't be done through the Settings/XFCE4 display, nothing loads! [/quote]

Not sure what's doing on with the settings utilities, but as a workaround what about this:

```
sudo dpkg-reconfigure xserver-xorg 
```

Select the resolutions you want with spacebar and enter to save and exit. 
I think that X defaults to the highest res selected from the list though, so bear that in mind.

[QUOTE=qwazert]
Where did the bottom toolbar go? [/quote]
I'm not sure if you're talking about the taskbar or the panel, but I think the panel is on the bottom by default. 

```
xfce4-panel & 
```

Should get it back.
As before, make sure you save your session so that the panel and taskbar/iconbox will be there for you on next login.


Hope this helps.

---

