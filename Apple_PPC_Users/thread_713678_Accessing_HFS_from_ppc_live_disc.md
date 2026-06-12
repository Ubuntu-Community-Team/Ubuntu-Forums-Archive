---
title: "Accessing HFS from ppc live disc"
date: 2008-03-03
forum: Apple PPC Users
---

### Post by artificialsteve on 2008-03-03
anyone have useful techniques for finding malicious OS X system hidden entries and or roots?  I suspect something is wrong on my machine, but I don't know what/where it is. 
This question is aimed at anyone with live cd skills!

---

### Post by stream303 on 2008-03-03
Without knowing what the problem is, I think your best bet would be to reinstall your original system.  Then, download and apply the latest **combo-update**, not the incremental one, and any security updates that are dated later than the last combo update.  (The combo updates include all the previous security updates)

When I was running OSX, I never performed the incremental automatic update and only let the update-notifier just tell me what was new.  I would opt out of the automated update process, and manually download and burn the Apple updates (especially the combo-updates, not incremental updates) from:

[http://www.apple.com/downloads/macosx/apple/](http://www.apple.com/downloads/macosx/apple/)

Be sure to download the combo updates that apply to your system, ie PPC, Intel, server, desktop, etc.  Burn the packages to cd/dvd so you don't have to download them all over again if you decide to reinstall.  Normally I just kept a burn of the latest combo update around.

One common suggested fix was to allow the system to fix your file permissions, but this in itself is a big security risk - file permission fixes can be tricked, and it is shocking to see it so widely recommended.

You might find
[http://www.macfixit.com](http://www.macfixit.com)
useful.

Or go ahead and take the plunge - let Ubuntu guided partitioning use the whole disk! :)

---

