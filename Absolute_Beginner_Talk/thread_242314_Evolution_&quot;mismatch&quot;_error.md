---
title: "Evolution &quot;mismatch&quot; error"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by walmartshopper67 on 2006-08-23
I use evolution (2.6.1), and I've never really used it before as I prefer thunderbird, but I need the calendar/task functions. I've been using it for about a week, but all of a sudden I'm getting this error: "Summary and folder mismatch, even after a sync". What does that mean, and how can it be fixed? Also, the junk filter doesn't seem to work at all - i get the same junk every day and keep pushing "mark as junk" but then the next day the same thing gets through. I'm not too concerned about that though, but the "Summary and folder mismatch, even after a sync" error is annoying, and I'm worried that I might be missing email because of that.

---

### Post by ahaslam on 2006-08-23
I randomly get the 'mismatch' error. When it happens I also get duplicates of any new messages.

I'd love to see a fix for this as I use Evoloution daily.

I hope that someone can help,

Tony.

---

### Post by walmartshopper67 on 2006-08-23
Well, I found a way to get rid of the error once it shows up: deleting the file ~/.evolution/mail/Inbox.ev-summary 

I found a bit about it here - [http://bugzilla.gnome.org/show_bug.cgi?id=213072](http://bugzilla.gnome.org/show_bug.cgi?id=213072)

I didn't *seem* to lose any mail after doing that, and it stopped the popup boxes (after restarting Evolution). Maybe it's fixed in Novell Evolution 2, which i havn't seen a package for Ubuntu.

---

### Post by danembraceddc on 2006-09-06
Works like a charm for me as well. thanks.

---

