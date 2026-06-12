---
title: "&quot;send link&quot; with Tbird 1.5 and FF 1.5"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by words1 on 2006-02-17
So I managed to install Thunderbird 1.5 in home/thunderbird, and even got a working icon in the top panel bar.  But when I try to "send link" from FF, I get nothing.  The Tbird thing in the bottom panel throbs, but no message to send opens (as it should).  I have Tbird entered as "custom" in Preferred Applications (with the link "/home/[user]/thunderbird/thunderbird, but apparently I'm missing something.  Help!

---

### Post by aysiu on 2006-02-17
Are you using Gnome or KDE?

---

### Post by kaamos on 2006-02-17
Try adding a " %s" to the end of the command in preferred applications.

---

### Post by words1 on 2006-02-17
" %s" worked!  Thanks!  What does that do?

Gnome, btw.

---

### Post by kaamos on 2006-02-17
I think it causes parameters being sent to the probram. So the command being run isn't only the name of the program, but more like "thunderbird -mailto address" or whatever the syntax of thunderbird is.

---

### Post by words1 on 2006-02-17
Thanks again.  This forum is awesome.

---

### Post by sailor2001 on 2006-02-17
I noticed that I had to remove the mozilla- infront of thunderbird % in prefered aplications

---

