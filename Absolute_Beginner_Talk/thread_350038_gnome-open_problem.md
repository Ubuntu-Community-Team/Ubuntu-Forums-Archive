---
title: "gnome-open problem"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Stettin on 2007-01-31
I recently upgraded my computer that had Dapper installed and formatted all partitions by my /home directory and installed Breezy. All of my bookmarks and things stayed, (which is good) but I had a few issues. One is that whenever I try to open a link from Gaim the firefox browser won't launch. I enabled the debug mode and saw it was using "gnome-open 'url address here'". I tried typing it out in a console window and get the following error..

Error showing url: There was an error launching the default action command associated with this location

Before in Dapper I had Firefox 1.5, then did an install of 2.0 and they both worked separately. I think this is related to the problem here. Any ideas how to change the "default browser" that gnome-open is trying to launch to match the Firefox 2.0 that is part of Breezy?

---

### Post by riven0 on 2007-01-31
Wait a minute, you went from Dapper to Breezy? Well, I would say that's part of the problem then Breezy has a lot of unfixed bugs in it that will stay unfixed.

---

### Post by irish_flu on 2007-01-31
riven-
If Stettin got Firefox 2.0 with the upgrade, I think s/he meant that s/he went from Dapper to Edgy.

Stettin-
Head over to the "System" menu, click "Preferences" and then "Preferred Applications".  Is "Firefox" already set to be the default browser, or is it something else?  I'd try playing with that selection a little, and see what happens.  I bet you're on the right track with wondering about there being some underlying problem with having the two separate browsers before the upgrade, but maybe setting something explicitly in "preferred applications" will take care of  it.

---

### Post by Stettin on 2007-02-01
Preferred Apps fixed it. It was set to "Custom" For web browser at /usr/opt/firefox, I switched it to just "Firefox" which was registered.

Thanks

---

### Post by irish_flu on 2007-02-01
No problem, glad to be of service!

---

