---
title: "How to put Network Manager icon on bottom panel?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bbqsandwich on 2008-02-18
How do I put the network manager icon -- the one that shows my wireless network signal strength in bars -- in the **bottom** panel rather than the top?

I tried right-clicking the bottom panel, choosing "Custom Application Launcher," and adding nm-applet, but it makes a spring icon (I assume that spring is the "launcher"), not the signal-bars icon I would like.

Thank you!

EDIT:

Yep, the tip below worked. I right-clicked my bottom panel, chose Add to Panel and chose the Notification Area under Utilities.

Then I right-clicked the top panel, deleted it, and restarted the computer. Voila!

---

### Post by spiderbatdad on 2008-02-18
it appears in the notification area. You will need to create one for the bottom panel. It may ultimately require a little tinkering with gconf-editor, if you try to delete the top panel entirely. Here's a screenshot of mine. You can see the notification area and nm-applet.

---

