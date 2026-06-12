---
title: "Firefox session restore"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by chris90uk on 2007-01-05
Hi,

Every time I start Firefox after I turn off my computer with it open, I get the annoying restore tabs box. I have gone into about:config and added new boolean things etc. as I have read online, but still it comes up and I don't know what to do now. Help would be appreciated, thanks.

---

### Post by Z(L)o on 2007-01-05
These are the settings to ACTIVATE that feature
I bet you have to change them to FALSE in order to deactivate:

type about:config in the address bar
find the following 

browser.sessionstore.enabled | Type: boolean | Value: true

browser.sessionstore.interval | Type: integer | Value: 30000 (equals 30 seconds, adjust to taste)

browser.sessionstore.resume_session | Type: boolean | Value: true

change to FALSE

hope it helps

---

