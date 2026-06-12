---
title: "Evince preferences"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by noynac on 2007-04-18
Evince remembers the last-viewed page of a previously-viewed PDF document and opens at that page when I reopen the document. By way of example:

1) I open the file xyz.pdf in Evince.

2) I scroll down to page 4.

3) I exit Evince.

4) I reopen file xyz.pdf in Evince and page 4 rather than page 1 is shown on the screen in Evince.

I did a google search on this and found that this is a feature that many find desirable. For me it's an annoyance. Evince does not have any preferences, and the configuration editor also does not seem to have any applicable Evince options.

How do I get Evince to always open a PDF document at page 1 rather than the last-viewed page?

BTW, I did a search of this forum and a google search on this topic, and I also looked at the Evince site, but could not find an answer to my question. Switching to a different PDF reader is not an option.

Thanks for the help!

---

### Post by RedSquirrel on 2007-04-18
I think it's built-in "feature" and there's no easy way around it.

It seems that that information is stored in ~/.gnome2/evince/ev-metadata.xml. You could write a script to delete that file, then run evince. Kind of drastic, but it works. You could also edit the source code for the program yourself and recompile (if you have any expertise in that sort of thing and if the licence grants you permission to do that).

For me, pressing Ctrl-Home is the easy way to get back to page 1. :)

---

### Post by noynac on 2007-04-18
RedSquirrel,

Thanks for the response. I sent an email to the evince developers asking that they incorporate some way to change the last-viewed page feature. Until then, I'll use ctrl-home.

Noynac

---

### Post by RedSquirrel on 2007-04-19
Excellent! I was going to suggest that you could contact the developers about this issue. 

As you wrote above, for some people it's useful, for others it's annoying. They really should have something in the UI to toggle it. It shouldn't be hard to add, IMO.

---

