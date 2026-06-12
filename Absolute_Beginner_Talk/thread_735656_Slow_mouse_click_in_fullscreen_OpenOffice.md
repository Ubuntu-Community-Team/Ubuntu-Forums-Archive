---
title: "Slow mouse click in fullscreen OpenOffice"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by DingsBumps on 2008-03-25
I'm using OpenOffice 2.3.0 on 64-bit gutsy with compiz enabled, and it's great until I get into fullscreen, at which point my mouse click becomes extremely laggy (at least 1 second behind my actual click). 
[LIST]
[*]The lag is apparent when clicking to reposition the cursor or click-dragging to select text. 
[*]The lag is not there when clicking on a box in floating toolbars (close fullscreen, styles, etc) while in fullscreen. 
[*]There is no problem in nonfullscreen
[/LIST]
Anyone have an idea?

---

### Post by c-ron on 2008-03-25
Hi,
Try this: Go to Compiz Config Panel -> Workarounds and disable Legacy full screen support
Post your findings here.

---

### Post by HunterK on 2008-03-25
Interesting find.  I just tested this out in 7.10 and there is definitely a lag only when in full screen mode. (Ctrl+Shift+J)  For me it is about .5 seconds when I click before the cursor will move there.  It is instant when not in full screen. :confused:

EDIT: and disabling legacy full screen did *not* work.

---

### Post by DingsBumps on 2008-03-26
Disableing legacy fullscreen support did not work.

Interesting find though-- I opened a new document and typed in 3 word, went full screen, and there was no (perceptible) lag. However, when I opened a longer document (2 pages), the .5-1 second lag was there again.

Perhaps if someone had a longer doc (like 10 pages? 20 pages?) and they also experience the same symptom (lag in fullscreen) they could test the longer docs and compare the lag to a shorter doc?

Also, I don't have any spreadsheets. There was no lag for me in an empty spreedsheet in fullscreen, but there also wasn't any lag in an empty text doc. Perhaps if someone who has a spreadsheet sitting on their HD and sees lag in oofice writer (hunterk?) could test for lag in oofice calc? Then we could see if the problem is spread out across all the oofice apps or just writer.

Thanks!

---

