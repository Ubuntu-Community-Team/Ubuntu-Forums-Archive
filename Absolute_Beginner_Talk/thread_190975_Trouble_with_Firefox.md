---
title: "Trouble with Firefox"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Joe t. on 2006-06-06
Hi. I just started using Ubuntu several weeks ago- no problems installing it on a Toshiba laptop. However, yesterday I was unable to start Firefox- a message said that the browser was already in use. Eventually, I was able to open it by creating another profile(user?). Anyway, all my bookmarks are on the first profile-at least I assume so. Does anyone know how to fix this? Thanks

---

### Post by aktiwers on 2006-06-06
Didnt the browser crash first? I have gotten this message after firefox crashed and all I had to do was to close firefox completely and open it again.

Close it 100% either pressing CTRL + ALT BACKSPACE and login again, or

Start Menu => System => Administration => System =>System Monitor

And close all Firefox stuff there. Hope it helps.

EDIT:

Else you can go to
Bookmarks =>Manage Bookmarks      => File => Import
And pick
 /etc/mozilla-firefox/profile/bookmarks.html

I think thats where it is.

---

### Post by Nano Geek on 2006-06-06
As your first user, try pressing **Alt-F2** and typing **killall firefox-bin** in the window that pops up. Then try opening Firefox again and see if it works.

---

### Post by Joe t. on 2006-06-06
I did crash the desktop once, and this happened after that. I tried what you said without success. However, with your second suggestion, I can't find system=>administration=>system. Any more ideas?

---

### Post by Joe t. on 2006-06-06
[QUOTE=asjdfwejqrfjcvm msz34rq33]As your first user, try pressing **Alt-F2** and typing **killall firefox-bin** in the window that pops up. Then try opening Firefox again and see if it works.[/QUOTE]
I tried that, and got the same browser. Any other ideas? Thanks.

---

### Post by aktiwers on 2006-06-06
Ups!! Sorry that was a typo. Should have been

Start Menu => System => Administration => System Monitor

Sorry for that :)

Does it still say that, even though you Kill Firefox completely?

---

### Post by aysiu on 2006-06-06
[QUOTE=Joe t.]I did crash the desktop once, and this happened after that. I tried what you said without success. However, with your second suggestion, I can't find system=>administration=>system. Any more ideas?[/QUOTE] There's no second *system*.

By the way, the bookmarks you want aren't in /etc. They're in your /home directory: ```
~/.mozilla/firefox/*profilename*/bookmarks.html
``` Your *profile* name will most likely be gobbledygook: *cdjn5lnckjls*, for example.

---

### Post by Joe t. on 2006-06-06
[QUOTE=aysiu]There's no second *system*.

By the way, the bookmarks you want aren't in /etc. They're in your /home directory: ```
~/.mozilla/firefox/*profilename*/bookmarks.html
``` Your *profile* name will most likely be gobbledygook: *cdjn5lnckjls*, for example.[/QUOTE]

I did find the bookmarks file and imported it. However, it does not contain the original bookmarks that I entered initially. ](*,)

---

### Post by Nano Geek on 2006-06-06
Try typing my original command in the terminal and tell us what it says.

---

### Post by Joe t. on 2006-06-06
[QUOTE=asjdfwejqrfjcvm msz34rq33]Try typing my original command in the terminal and tell us what it says.[/QUOTE]

I did as you said, and the browser closed. There was no message.

---

### Post by Nano Geek on 2006-06-07
Try typing **firefox -d** in the command line and then posting what the command line says after Firefox crashes.

---

