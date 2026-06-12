---
title: "SIGSEGV or SIGBUS error when running a backup"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by keith whitehouse on 2006-06-01
Following Helios backup guide.

My terminal input is

tar cvpjf backup.tar.bz2 / --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /

the last few lines of the Terminal output are

/home/keith/.mozilla/
/home/keith/.mozilla/firefox/
/home/keith/.mozilla/firefox/profiles.ini
/home/keith/.mozilla/firefox/ca2819ii.default/tar cvpjf backup.tar.bz2 / --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt  --exclude=/sys /
/home/keith/.mozilla/firefox/ca2819ii.default/chrome/
/home/keith/.mozilla/firefox/ca2819ii.default/chrome/userChrome-example.css/home/keith/.mozilla/firefox/ca2819ii.default/chrome/userContent-example.css/home/keith/.mozilla/firefox/ca2819ii.default/bookmarks.html
/home/keith/.mozilla/firefox/ca2819ii.default/localstore.rdf
/home/keith/.mozilla/firefox/ca2819ii.default/mimeTypes.rdf
/home/keith/.mozilla/firefox/ca2819ii.default/prefs.js
/home/keith/.mozilla/firefox/ca2819ii.default/search.rdf
/home/keith/.mozilla/firefox/ca2819ii.default/.parentlock
/home/keith/.mozilla/firefox/ca2819ii.default/compatibility.ini
/home/keith/.mozilla/firefox/ca2819ii.default/compreg.dat
/home/keith/.mozilla/firefox/ca2819ii.default/xpti.dat
/home/keith/.mozilla/firefox/ca2819ii.default/extensions/
/home/keith/.mozilla/firefox/ca2819ii.default/extensions.rdftar cvpjf backup.tar.bz2 / --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt  --exclude=/sys /
/home/keith/.mozilla/firefox/ca2819ii.default/extensions.cachetar cvpjf backup.tar.bz2 / --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt  --exclude=/sys /
/home/keith/.mozilla/firefox/ca2819ii.default/extensions.ini
/home/keith/.mozilla/firefox/ca2819ii.default/XUL.mfasl
/home/keith/.mozilla/firefox/ca2819ii.default/secmod.db
/home/keith/.mozilla/firefox/ca2819ii.default/cert8.db
/home/keith/.mozilla/firefox/ca2819ii.default/key3.db
/home/keith/.mozilla/firefox/ca2819ii.default/history.dat
/home/keith/.mozilla/firefox/ca2819ii.default/bookmarkbackups/
/home/keith/.mozilla/firefox/ca2819ii.default/bookmarkbackups/bookmarks-2006-05-29.html
/home/keith/.mozilla/firefox/ca2819ii.default/bookmarkbackups/bookmarks-2006-05-30.html
/home/keith/.mozilla/firefox/ca2819ii.default/bookmarkbackups/bookmarks-2006-05-31.html
/home/keith/.mozilla/firefox/ca2819ii.default/bookmarkbackups/bookmarks-2006-06-01.html
/home/keith/.mozilla/firefox/ca2819ii.default/bookmarkbackups/bookmarks-2006-05-28.html
/home/keith/.mozilla/firefox/ca2819ii.default/Cache/
/home/keith/.mozilla/firefox/ca2819ii.default/Cache/_CACHE_MAP_
/home/keith/.mozilla/firefox/ca2819ii.default/Cache/_CACHE_001_
/home/keith/.mozilla/firefox/ca2819ii.default/Cache/_CACHE_002_
/home/keith/.mozilla/firefox/ca2819ii.default/Cache/_CACHE_003_

bzip2: Caught a SIGSEGV or SIGBUS whilst compressing.

   Possible causes are (most likely first):
   (1) This computer has unreliable memory or cache hardware
       (a surprisingly common problem; try a different machine.)
   (2) A bug in the compiler used to create this executable
       (unlikely, if you didn't compile bzip2 yourself.)
   (3) A real bug in bzip2 -- I hope this should never be the case.
   The user's manual, Section 4.3, has more info on (1) and (2).

   If you suspect this is a bug in bzip2, or are unsure about (1)
   or (2), feel free to report it to me at: [email]jseward@bzip.org[/email].
   Section 4.3 of the user's manual describes the info a useful
   bug report should have.  If the manual is available on your
   system, please try and read it before mailing me.  If you don't
   have the manual or can't be bothered to read it, mail me anyway.

        Input file = (stdin), output file = (stdout)
keith@ubuntu:~$

I have just installed Kdar and have tried to make a backup, but it too comes to a stop with the signal 11 SIGSEGV.

I have used the Helios method a few times without any problems, so I assume that it is something that I have done over the past few days.

I could not get one of the programs (ProjectX) that I need to run in Ubuntoo (Dapper Drake Beta) so in the end out of sheer desperation I downloaded Java JDK and compiled it myself using a guide I found on MythTV, and much to my surprise and delight ProjectX runs.

I have tried to install some windows programs to run under Wine, could this be something to do with the error. How do I install Windows.exe files into Ubuntoo. One of the programs is on 3 floopy discs?

I have only been with Ubuntoo about 4 weeks and when I was using Breezy 5.10 I made so many mistakes that I had to re-install it several times, and at present I am using Dapper Drake Beta which has hundreds of updates installed to it, so could any of these be responsible.

At worse if I can't resolve the problem I will download the new full Dapper Drake and start again from scratch

best regards keith

---

