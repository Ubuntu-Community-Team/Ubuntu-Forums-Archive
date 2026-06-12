---
title: "User Time Limits"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by laytek on 2006-11-16
Hello everyone,
I have recently loaded Dapper on a 3 year old HP Pentium 4. I love it!

Turns out that the kids love Ubuntu also. Maybe a little too much! [http://ubuntuforums.org/images/smilies/icon_confused.gif](http://ubuntuforums.org/images/smilies/icon_confused.gif)

Question: Is there a method or system to limit the time a user can be logged into the system? Specifically, I want to limit the kid's logins to one hour  each weekday, and 2 or 3 hours each weekend day.

Thanks to all.

Alan

---

### Post by davmac on 2006-11-18
I think you can use PAM for this. Have a look at [http://www.debian-administration.org/articles/227](http://www.debian-administration.org/articles/227) for a guide to setting up.

Dave Mac

---

### Post by asease on 2007-12-30
I used TIMEOUTD successfully.  You can load it through the Package Manager, then edit the file to suit your needs.

HTH!
Alan

---

### Post by Joeb454 on 2007-12-30
asease are you REALLY still using Hoary (5.04)?!?!?!

Sorry for the off topic post :)

---

