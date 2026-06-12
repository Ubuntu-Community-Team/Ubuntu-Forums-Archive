---
title: "Google Desktop Search: indexing root"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by petit.padavoine on 2007-07-13
By default, Google Desktop Search for linux indexes the following directories:
/home/<youruser>
/usr/share/info
/usr/man
/usr/share/man
/usr/local/share/man
/usr/local/man
/usr/X11R6/man

I want it to index my whole filesystem, so I added / to the list of places to index as soon as I installed it.

A few hours later, I looked at the Index Status window, which said it was done indexing.

However, only the files in the default directories listed above were indexed.

How can I get Google Desktop Search to index my whole filesystem?

---

### Post by 56seeker on 2007-07-13
Do you have rights to the whole file system?

That may be what google is tripping up over.

---

### Post by petit.padavoine on 2007-07-13
I thought that might be the issue.

I have administrator privileges, but when Google Desktop Search launches, it doesn't ask for them.

Should I add gksudo to the beginning of the command executed at startup, i.e. instead of "<launch google desktop search>" "gksudo <launch google desktop search>"?

I'll try that. Thanks.

---

### Post by hackle577 on 2007-07-13
Also, check to make sure you haven't disabled searching in some directories through your Google Desktop preferences page.

---

### Post by petit.padavoine on 2007-07-31
Well I just added / without touching any of the defaults, so it should index it...

---

