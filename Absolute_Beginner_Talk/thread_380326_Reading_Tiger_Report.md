---
title: "Reading Tiger Report"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-03-09
I ran Tiger to check for system vulnerabilities. 
When it finished, instead of showing the report in the Terminal,  it said the report could be found in:  /var/log/tiger/security.report. The report is there but when I try to open it, I get the message: "Cannot open. No application suitable for automatic installation is available for handling this kind of file."
Can someone suggest a suitable application or work-around?
Thanks

---

### Post by taurus on 2007-03-09
You can't open it with more!

Applications -> Accessories -> Terminal
```
more /var/log/tiger/security.report
```

---

### Post by Stunt Double on 2007-03-09
Thanks Taurus.
With sudo more /var... it did work. 
I wonder why they made it so difficult to read the report?
But once again everything looks good. 
So far, I've run f-prot, rkhunter, chkrootkit, and, of course, tiger.
No problems reported.
Ubuntu Edgy Eft continues to amaze me.

---

