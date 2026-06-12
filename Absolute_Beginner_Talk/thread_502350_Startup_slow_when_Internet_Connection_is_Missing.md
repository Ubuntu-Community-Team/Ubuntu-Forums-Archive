---
title: "Startup slow when Internet Connection is Missing"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by becominglumberg on 2007-07-16
Hey-
This isn't a huge deal, but I have found that my computer starts (and subsequently runs) VERY slowly whenever   it is disconnected from the internet. Normally, from password to GNOME being completely ready takes ten seconds or less. If the internet is unplugged, it will take at least 3 minutes and a glass of water.

Anybody knows what gives?

---

### Post by DBStevens on 2007-07-16
Sounds like it is trying to get an IP lease and can't and retrying several times after a timeout period before giving up and going on..

You could look for the timeout values and lower them or decrease the number of retries etc....

---

