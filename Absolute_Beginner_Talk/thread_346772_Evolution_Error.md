---
title: "Evolution Error"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Rollotamasi on 2007-01-26
When I shut my computer down last night everything was running fine.  When I started up this morning my evolution e-mail client started getting a error.  It pops up a window that says "Error while storing folder inbox, Summary and folder mismatch even after sync"  After I click the OK button it goes away for about 5 mins then comes back again.  The client itself seems to be working, I can still send and receive mail but random program errors make me nervous.

Any suggestions?

Thanks!

---

### Post by crossedout on 2007-01-26
Try deleting the file ~/.evolution/mail/Inbox.ev-summary

You'll need to restart Evolution as well.

-Xout

---

### Post by jongkind on 2007-01-26
I had this some time ago. One drastic solution:


[LIST=1]
[*]Close Evolution
[*]Copy your Evolution profile (~/.evolution) to the desktop.
[*]After that remove the profile frome your home folder.
[*]Restart Evolution and you will be asked to fill in the account settings
[*]Import the mailfolder from your desktop (look for the files in ~/.evolution//mail/local/) into Evolution again via the menu option File-import
[/LIST]


I hope this helps

---

### Post by jnjintc on 2007-06-10
Whenever I clicked on my inbox I got the Evolution Error popup and evolution froze. This 'drastic' solution work like charm. 

thank you

---

