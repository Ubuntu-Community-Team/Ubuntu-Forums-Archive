---
title: "Why the font size in the menu of firefox is larger than the system font size?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by yuliang on 2006-10-17
The font size on the menu of firefox is always larger than the system fonts in Xubuntu. The system font sizes increase, the font size on the menu increases, but always larger. Why? How to change the menu font sizes?:rolleyes:

---

### Post by crimson on 2006-10-25
Yeah, I'm seeing the same thing here. Does anyone have an answer? Even a suggestion? Thanks!

To clarify, changing the font selections in Firefox's Preference window have no effect, while changing the font size in xfce's settings *does* have an effect, but the size is always about 4 pts larger than it should be. (I have mine set for Sans 12, and the font in the Firefox menu, dialogs, and text entry boxes looks to be about 16 point.

---

### Post by lerio on 2007-02-17
same problem here. pretty annoying

---

### Post by capital on 2007-02-19
The problem is with Firefox, not the system.  Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

### Post by kerry_s on 2007-02-19
I use it to my advantage combing it with userChrome.css(.mozilla/firefox/?.default/chrome/) using 2 sizes.

---

### Post by zba78 on 2007-02-28
> **capital said:**
> The problem is with Firefox, not the system.  Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox
Thank you **capital**. That did the trick

---

