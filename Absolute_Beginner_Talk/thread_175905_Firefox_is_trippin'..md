---
title: "Firefox is trippin'."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-05-14
So Firefox is the standard browser.

I'll be browsing along and browsing along and suddenly BAM - ...It just exits. By itself. Everything is gone.

Sometimes I can tolerate it, but sometimes when I'm trying to make a long post and I click the 'submit' button, bye bye everything I just wrote. ](*,) 

Is this normal? Is there a way to iron it out?

Oh, and another Firefox problem - I change the settings to make it so whenever a new link is clicked to a new website, it makes a new tab in the most recent browser - but it never happens. What's the deal.

---

### Post by nanotube on 2006-05-14
hmm, that is strange, and hard to diagnose.
well, you could run firefox from a terminal, and then wait until it crashes, and see if there are any indicative error messages left over in that terminal.

or if you want to forgo the diagnostic step, and just try fixing it by poking blindly, you can try:
- backing up and wiping your .mozilla directory with the firefox preferences (basically, mv .mozilla .mozilla-backup), and try and see if that helps
- uninstall some extensions that you have installed
- upgrade to the newest version of firefox, if you haven't already (1.5.0.3)

---

### Post by aysiu on 2006-05-14
For the crashing, try [this](http://www.ubuntuforums.org/showthread.php?t=103930). For the tab thing, try [this](https://addons.mozilla.org/firefox/1122/).

---

### Post by Elim on 2006-05-14
The Tab Mix extension that aysiu posted is one option.  I've used the SessionSaver extension ([https://addons.mozilla.org/firefox/436/](https://addons.mozilla.org/firefox/436/)) for a long time now with no problems.  It will open Firefox with whatever tabs were open when it closed, and with forms filled out as well (such as the box that I am typing this post in).  It's gotten me through many crashes.  In addition, there is also a third extension that addresses this issue, Crash Recovery ([https://addons.mozilla.org/firefox/1955/)](https://addons.mozilla.org/firefox/1955/)).

Note: I only just learned of Tab Mix Plus and Crash Recovery while researching for this post.  I've used SessionSaver for a long time, so I know it is very reliable, but I can't speak to the other two, or make comparisons between the three.  Sorry.

---

