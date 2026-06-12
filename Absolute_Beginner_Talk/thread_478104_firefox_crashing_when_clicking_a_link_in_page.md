---
title: "firefox crashing when clicking a link in page"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by randy_pierson on 2007-06-19
I am using Ubuntu Fiesty, Firefox with installed add-ons, Adblock  Plus, Cooliris, Flashblock. on Myspace.com, when trying to click onto a friend, Firefox loads about 10% and then crashes. it doesn't happen with all friends, but is consistant  with the friends that cause the crash. Firefox's error console has alot of errors with "unknown property '_width'. declarations dropped" and it gives a link showing the css form of the page. I checked Firefox forums and other Linux users seem to be having similar problems. I was curious if anyone could give a little insight to what could be causing this problem. Everything worked fine about a week ago.

---

### Post by Crafty Kisses on 2007-06-19
> **randy_pierson said:**
> I am using Ubuntu Fiesty, Firefox with installed add-ons, Adblock  Plus, Cooliris, Flashblock. on Myspace.com, when trying to click onto a friend, Firefox loads about 10% and then crashes. it doesn't happen with all friends, but is consistant  with the friends that cause the crash. Firefox's error console has alot of errors with "unknown property '_width'. declarations dropped" and it gives a link showing the css form of the page. I checked Firefox forums and other Linux users seem to be having similar problems. I was curious if anyone could give a little insight to what could be causing this problem. Everything worked fine about a week ago.

You should see all the processes you have running at the time of the crash, if you have 99% CPU usage at the time, it will obviously crash.

To check your processes, open up terminal and type:
```
top
```

That should tell you what you have running.

---

### Post by suhanduman on 2007-06-19
Plus you have to run a memtest IMHO. 
You can select memtest from grub menu.

---

### Post by Golyadkin on 2007-06-19
I had this bug in Windows sometimes too, it seemed to be segfaulting. In Ubuntu however, on the same pc, it never happened. And memtest runs without errors for 24 hours.

---

