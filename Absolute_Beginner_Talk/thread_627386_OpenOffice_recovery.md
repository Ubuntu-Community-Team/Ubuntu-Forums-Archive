---
title: "OpenOffice recovery?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-11-30
Hi.
I opened a file that i downloaded from out school's website and I continued to write on it and I saved it every now and then. But it was saved in /tmp/... Is it impossible to recover what i wrote with openoffice?

---

### Post by Sef on 2007-11-30
So the document is still on the school's computer?

---

### Post by spydon on 2007-12-02
> **Sef said:**
> So the document is still on the school's computer?

No, it was on my computer in /tmp/
But after I rebooted it was gone ofc. :P
It is unrecoverable isn't it?

---

### Post by mahiyar on 2007-12-02
As the name suggests /tmp is meant to be temporary storage of files which every user can share and refreshes on every reboot. If the changes you made were very important google for file recovery programmes, I'am sure there are some, or best forget and learn.

---

### Post by spydon on 2007-12-02
> **mahiyar said:**
> As the name suggests /tmp is meant to be temporary storage of files which every user can share and refreshes on every reboot. If the changes you made were very important google for file recovery programmes, I'am sure there are some, or best forget and learn.

It wasn't much in the document and I think the things I wrote will be written even better this time. Thx for your answer's anyway!

---

### Post by schorsch on 2007-12-02
/tmp is deleted at every reboot per default. "man rcS" in a terminal gives this information:
```
TMPTIME On  boot  the  files  in  /tmp will be deleted if their modification time is more than TMPTIME days ago.  A value of 0 means that files are removed regardless of age.  If you don&#8217;t want the system to clean /tmp then set TMPTIME to a negative value (e.g., -1) or to the word infinite.
```
To change this behaviour you have to edit the file "/etc/default/rcS".

---

