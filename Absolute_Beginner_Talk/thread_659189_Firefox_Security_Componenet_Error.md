---
title: "Firefox Security Componenet Error"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by rainchyld79 on 2008-01-05
Hi, everyone. I've been on Gutsy Gibbon for about a month or so now and I absolutely love it.

Last night, after having been able to successfully launch Firefox with no issues at all since I first installed Ubuntu, I (seemingly randomly) received the following error:
[I]
Could not initialize the browser's security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory as no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behavior when accessing security features.[/I]

I click OKAY - Firefox never opens though. So far I haven't been able to find other threads that have this specific problem so I'm posting here, at the suggestion of my boyfriend. Thank you in advance!

---

### Post by FuturePilot on 2008-01-05
It sounds like something wrong with your Firefox profile. Try creating a new one
```
mv .mozilla .mozilla_old
``` 
This will rename your current profile so that when you start Firefox it will create a new one. If it works you can recover your bookmarks by pressing Ctrl+H in your home folder to show hidden files, then find the .mozilla_old folder and find the bookmarks.html file and move it to the new profile in the .mozilla folder. Make sure to shut down Firefox before moving the file or else it will get overwritten when you close Firefox.

---

### Post by eternicode on 2008-01-05
BTW, the firefox profile folders are in ~/.mozilla/firefox/, not ~/.mozilla

---

