---
title: "Firefox font too small"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-07-30
Hi, how do I change the font size permanently in firefox? Everytime I close firefox and start it up again it goes back to the small text size, and I need to make it bigger again. Thanks

---

### Post by x64Jimbo on 2006-07-30
Edit > Preferences > Content

---

### Post by snellgrove on 2006-07-30
How are you changing the fonts normally?

does it save other settings, or is it losing just this font setting each time? (try changing your home page for example - see if it persists)

I dunno if this will work, but what if you run firefox as the root user once,  visit a trusted site such as [http://www.google.com](http://www.google.com) and then change the font size, exit firefox and then run it as you.

See if the changes are still there. just wondering if this is some 'permissions' style problem, where your font settings aren't being saved for whatever reason.

To launch firefox as root, open a terminal and type in:```
sudo firefox
```

Also you could try opening Synaptic, and doing a Reinstall.

If that doesn't work remove the /home/*username*/.mozilla/firefox folder.

This will reset your firefox to standard's though (your extensions, themes,  bookmarks, cookies, cache, history  etc will be gone! so make a backup first.)

If that doesn't work, open Synaptic and do a 'Complete Removal' of firefox and then re-installing.

Unfortunately this will no doubt remove half of the things dependant on firefox :( so they'll need to be installed again.

other than that, maybe someone else has a better idea of how to fix this. I dont know for sure, this is just a list of suggestions :lol:

---

### Post by dlocutor on 2006-07-30
.. Try:
  Edit -> Preferences -> Content -> Default Font settings ..

---

### Post by x64Jimbo on 2006-07-30
Each user has a different firefox profile, so using it in root will not make any difference.

---

### Post by x64Jimbo on 2006-07-30
> **dlocutor said:**
> .. Try:
  Edit -> Preferences -> Content -> Default Font settings ..
I said that already. First reply.

---

### Post by wsun on 2006-07-31
here's a screenshot, I tried changing the font size in preferences and it didn't work

---

### Post by guopai on 2006-07-31
I think you need to force browser to always use your own font setting.

Go to Edit > Preferences > Content, then click "Advanced" under "Fonts & Colors." Choose the language "Western," then adjust font sizes, including minimum font size, and untick "Allow page to choose their own font..." The downside is that every site will use the same font you specified. I don't know if there's any other way around.

---

### Post by kerry_s on 2006-07-31
Try the firefox extension called nosquint-> [http://urandom.ca/nosquint/](http://urandom.ca/nosquint/)
or from the mozilla site-> [https://addons.mozilla.org/firefox/2592/](https://addons.mozilla.org/firefox/2592/)

---

### Post by tenkamuteki82 on 2007-11-01
YES THANK YOU SO MUCH!! Nosquint... Ive been stuck on this for months and was going blind... I even switched to 640x480 resolution for this...

THANK YOU for your very helpful knowledge.

---

### Post by kooldino on 2007-11-19
I guess nosquint does the trick...Opera doesn't have this issue though.

---

### Post by x64Jimbo on 2007-11-19
You can also hold down the Ctrl button while scrolling your mouse wheel.

---

