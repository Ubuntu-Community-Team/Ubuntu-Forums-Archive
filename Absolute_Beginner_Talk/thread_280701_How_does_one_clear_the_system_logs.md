---
title: "How does one clear the system logs"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by emarkay on 2006-10-19
They grow daily, but other than manually deleting them, can one selectively 'gooey' them into oblivion, especialy the older ones?

---

### Post by po0f on 2006-10-19
emarkay,

Most of the programs that log stuff are automatically rotated via [logrotate](http://packages.ubuntu.com/dapper/admin/logrotate).  Most of the time, it will rotate logs weekly.  First, the current log is gzipped and named something like log.1.gz.  If there is already a file named that it gets bumped to log.2.gz, and so on up to 4.  So you should have a current log file, and four gzipped log files from the previous month IIRC.  You can edit the logrotate rules for more aggresive rotating if you're worried about space.

If you need help writing an entry for a program whose logs you would like rotated, post back.

---

### Post by emarkay on 2006-10-19
Wow, I would have prob never figured that one out on my own.  

I'll watch for a while and see if these rotated archives build up to where I decide to send them back to random bits. 

Ther's no logging of logs whereby a manual delete of the old ones will cause some unpleasant reaction somewhere, is there?  :)

Thanks, this Linux stuff is so invigorating.

---

