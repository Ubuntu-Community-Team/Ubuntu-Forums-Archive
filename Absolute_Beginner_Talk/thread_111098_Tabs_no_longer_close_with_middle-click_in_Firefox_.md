---
title: "Tabs no longer close with middle-click in Firefox 1.5"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Gimbo on 2006-01-01
I installed Firefox 1.5 following the instructions from [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion").

Everything seems to be OK, except that when I middle-click on tabs, rather than closing them, Firefox navigates to Yahoo.com.

Any help would be greatly appreciated.

Update: I'm now getting an "Alert" box with the error "The URL is not valid and cannot be loaded." when middle-clicking on tabs.
Update2: Now nothing happens when middle-clicking on tabs.
Update3: Now it reloads the page - this is getting bizarre.

---

### Post by Mustard on 2006-01-01
A corrupted extension perhaps?

What extensions do you have installed that work with the tabs?

---

### Post by Gimbo on 2006-01-01
Just the ones that were installed by default (DOM Inspector and Talkback).

---

### Post by Omnios on 2006-01-01
Try firefox preferences and tabs, also if you loaded an extension it may be a culprit

---

### Post by Pluk on 2006-01-01
Middlemouse button behaviour on the tab is paste in 1.5. You can change it back:
In the location bar write: about:config

Then in the filter bar write : middlemouse
In middlemouse.contentLoadURL change true to false (doubleclick true)

After this you can close tabs the old way.

---

### Post by Gimbo on 2006-01-01
Edit>Preferences>Tabs

Open links from other applications in:
a new tab in the most recent window

Force links that open new windows to open in:
[unchecked]

Hide the tab bar when only one web site is open:
[checked]

Select new tabs opened from links:
[unchecked]

Warn when closing multiple tabs:
[checked]

There don't seem to be any relevant options there, and I've searched high and low in the Firefox menus and it seems that keyboard/mouse shortcuts are fixed (ie non-configurable).

---

### Post by Mustard on 2006-01-01
[QUOTE=Pluk]Middlemouse button behaviour on the tab is paste in 1.5. You can change it back:
In the location bar write: about:config

Then in the filter bar write : middlemouse
In middlemouse.contentLoadURL change true to false (doubleclick true)

After this you can close tabs the old way.[/QUOTE]

Ah ok...I didn't know that. :)

---

### Post by Gimbo on 2006-01-01
Pluk, you're a genius - thanks!

I don't think they've changed the defaults for the Windows version of 1.5, and I can't really see how it's an improvement. Still, I'm sure the nice people at Mozilla know what they're doing.

---

