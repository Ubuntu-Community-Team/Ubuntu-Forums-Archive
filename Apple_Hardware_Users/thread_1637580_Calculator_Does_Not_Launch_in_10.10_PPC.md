---
title: "Calculator Does Not Launch in 10.10 PPC"
date: 2010-12-04
forum: Apple Hardware Users
---

### Post by funnysnoot on 2010-12-04
When I try to launch the Calculator from the Applications menu I get the "Starting Calculator" tab in the bottom panel, but the application never launches and the tab disappears after a few seconds.

Anybody have this problem or know how to solve it?

---

### Post by shawnhcorey on 2010-12-04
Try launching it from a terminal to see if it outputs any error message.

---

### Post by funnysnoot on 2010-12-04
So I typed in gcalctool in terminal and got the following:

GLib-GIO-ERROR **: Settings schema 'org.gnome.gcalctool' is not installed

aborting...
Aborted

---

### Post by shawnhcorey on 2010-12-04
This may help:  [http://ubuntuforums.org/showthread.php?t=1568056](http://ubuntuforums.org/showthread.php?t=1568056)

---

### Post by funnysnoot on 2010-12-04
Thanks for the input shawnhcorey, but, alas, still getting the same error message. Basically the gist of the thread you referred to instructed me to install/purge empathy and gcalctool. Interestingly, I get the same error when I try to launch empathy. Now, I wonder...what are the "settings schema" I am missing for these packages?

---

### Post by shawnhcorey on 2010-12-04
I have no idea what's wrong or what the error messages mean.  Running the app in a terminal often gives you an error message you can google for, to see if anyone else has the same problem.  Beyond that, I don't know.

---

### Post by funnysnoot on 2010-12-04
After some extensive Googling, I found a thread on bug.launchpad.net that suggested I enable the maverick-proposed repository and update the glib 2.26 package. I did that, and it seems the problem has been solved.

Hopefully, someone else who runs into this same issue finds this thread helpful.

Nevertheless, thanks for answering my question shawnhcorey.

---

