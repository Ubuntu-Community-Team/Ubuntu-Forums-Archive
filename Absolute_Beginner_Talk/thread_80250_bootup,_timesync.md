---
title: "bootup, timesync"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by susa on 2005-10-21
hello,

just installed (today) 5.10 from a cd I downloaded 

my system is a corporate desktop and thus I went into the network settings and created a proxy connection with userid/password (same in firefox) 

but, what is annoying is the timesync always REDlining at bootup (of course!) since it is unable to connect to any ntp server

in CentOS and Gentoo I can turn this off as root, what's the BreezyBadger way of doing it (the "do not timesync at bootup") ?

I did read this thread
[http://www.ubuntuforums.org/showthread.php?t=16668&highlight=timesync](http://www.ubuntuforums.org/showthread.php?t=16668&highlight=timesync)

---

### Post by Lambert on 2005-10-21
google the term [update-rc.d -f ntpdate remove]("http://http://www.google.com/search?hl=en&q=update-rc.d+-f+ntpdate+remove&btnG=Google+Search") or go to the man page for update-rc.d

You may find your answer there.

---

