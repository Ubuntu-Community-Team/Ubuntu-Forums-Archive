---
title: "Thunderbird folders"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by acbrady on 2007-04-15
I have suddenly  lost all the folders, excepting 'inbox' in Thunderbird running on 6.06.
any ideas?

---

### Post by vanadium on 2007-04-15
No idea at all. Your thunderbird settings, including your mail folders live under

~/.mozilla-thunderbird/[randomstring].default/

Local mail is under

Mail/Local Folders

I copied my mail folders from my Windows system under that directory, and Thunderbird picked them up. The only caveat is that they must have read/write permissions. In my first attempt, the mail files were read-only, and then they are not picked up.

* Check these folders. The email files have the names as they appear in Thunderbird, e.g., I have a "2007 in" and a "2007 out" file amongst others.

* Under Edit - Account settings - Local folders, check that "Local directory" points to the correct folder, e.g.
/home/USER/.mozilla-thunderbird/RANDOM_STRING.default/Mail/Local Folders

If it is the folders of an IMAP acccount that disappeared, then it could be an issue with your mail server.

---

