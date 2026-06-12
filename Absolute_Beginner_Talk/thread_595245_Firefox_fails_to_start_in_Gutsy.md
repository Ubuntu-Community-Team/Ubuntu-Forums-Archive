---
title: "Firefox fails to start in Gutsy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Kale26 on 2007-10-28
I had a number of video problems installing Gutsy straight up, so I installed a command line system, then installed the destop via aptitude.  Now everything is working fine, except firefox doesn't start.  I click on the Firefox icon in the desktop and get a 'starting firefox' tab in the status bar below, the hourglass churns for a bit, then the tab vanishes and nothing else happens.  When I type firefox into a terminal I get the error message:

(firefox-bin:6560): Gtk-WARNING **: cannot open display:

I've had a lot of problems with this install, but so far this is the only one that's stumped me!  Please help!

---

### Post by Kale26 on 2007-10-28
Whoops!  I seem to have fixed it.  One of the other posts on the forum mentioned deleting your .mozilla folder.  After I did that (after figuring out how to chmod it so I could get to it!) firefox started up OK.
Now, can somebody tell me what the heck I did by deleting .mozilla, and why it made firefox work?

---

### Post by alienexplorers on 2007-10-29
You basically deleted a bad profile and firefox created a new one.  It's one way to fix your type of problem.

---

