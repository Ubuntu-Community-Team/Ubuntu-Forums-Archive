---
title: "Tabs in firefox"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by codeking on 2007-09-12
I went in to Preferences in Firefox and set it up to open links in new tabs instead of opening up a window, but it still opens up new windows.  Why is this happening?

---

### Post by Maestro23 on 2007-09-12
> **codeking said:**
> I went in to Preferences in Firefox and set it up to open links in new tabs instead of opening up a window, but it still opens up new windows.  Why is this happening?

Yeah, this has been brought up before.  Don't know if it's a Ubuntu thing or FF issue.  You can d/l and extension called Tab Mix Plus and your tabs will work correctly.

In FF:  Tools>> Add-Ons>> Get Extensions

---

### Post by vanden12 on 2007-09-12
THe built in tab support for firefox is not that great...Your best of getting Tab Mix Plus like said above it will do alot more for you...

---

### Post by MobiusNZ on 2007-09-12
Its probably because those links are popup links... you can further customise the handling of popups by typing in 
```
about:config
```
into your address bar. Type "window" in the filter, and you will be on the right track. Google the likely preference to find out what the values mean.
[[COLOR="Red"]This[/COLOR]]("http://kb.mozillazine.org/Browser.link.open_newwindow.restriction") might be a good place to start.

---

### Post by nick_h on 2007-09-13
This is a known problem.  Change back to opening in a new window and then back again to opening in a tab and it should fix the problem.

---

### Post by CaptainInsaneO on 2007-09-13
If you have a scroll wheel on your mouse, you can click the link with your wheel and it will open the link in a new tab.

You can also click the tab with your wheel and it will close the tab.

---

### Post by lightstream on 2007-09-15
> **MobiusNZ said:**
> Its probably because those links are popup links... you can further customise the handling of popups by typing in 
```
about:config
```
into your address bar. Type "window" in the filter, and you will be on the right track. Google the likely preference to find out what the values mean.
[[COLOR="Red"]This[/COLOR]]("http://kb.mozillazine.org/Browser.link.open_newwindow.restriction") might be a good place to start.
The setting you need is 
```
browser.link.open_newwindow
```
Setting it to 3 made new windows open in tabs like they should do

> **browser.link.open_newwindow [Integer]** - This setting determines where hyperlinks which would normally open in a new browser window end up opening. If set to 1, they open in the current Firefox window; if set to 2 they open in a new window; and if set to 3 (the default) all such links open in a new tab in the current Firefox window. Note that this setting is the same as that found under the in-browser Options>Tabs screen, however there is an additional choice here (setting it to 1).

---

