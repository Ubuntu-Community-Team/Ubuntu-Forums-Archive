---
title: "System slows down after a day working"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-12-11
After a day of working system becomes almost unusable. - All programs hang up, interface reacts painfully slow, even the mouse cursor.
The HDD light is constantly on as if the system is constantly swapping memory. 
System-monitor resources tab says that 800MB of my 1GB memory is used (but at startup it was only 400 and I haven't launched new programs). But if I sum memory used by all processes I'll get only about 300MB - where are the other 500?

---

### Post by FakeOutdoorsman on 2007-12-12
Try opening a terminal and use the "top" command.  It will show a list of tasks usually sorted by CPU usage which might be able to point you to the resource hog.

---

### Post by kpkeerthi on 2007-12-12
[Where did my memory go?]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

---

### Post by beniwtv on 2007-12-12
Hey netimen,

Are you by any chance running the desktop effects with a Nvidia card?

If yes, this bug report may help you: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151168)

Hope this helps.

---

### Post by netimen on 2007-12-12
thank you, beniwtv. I really use compiz with an NVIDIA card, but I'm afraid I have another issue - according to top my compiz uses only 200MB, but my java ~1200!
Also there is a strange mismatch between top and system-monitor information. s-m says java uses only 80 and compiz only 20MB

So, I think Java appears to be the most memory consuming application. I have amarok and azureus, wich use java.

---

### Post by netimen on 2007-12-12
.

---

### Post by beniwtv on 2007-12-14
Hey netimen,

The difference between System monitor and top is that in top the "virtual memory" is displayed, and in System monitor it is not by default (it only displays real memory).

You can enable it by going to Edit->Preferences, and select "Virtual Memory" under "Process information".

Also, that java is using so much memory is not very normal. Do you view much java sites, or use java programs?

---

### Post by philinux on 2007-12-14
Azureus is buggy and can be a resource hog because it uses java.

Try Deluge to see if that improves things.

---

