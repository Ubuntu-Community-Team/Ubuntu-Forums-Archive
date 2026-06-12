---
title: "Too many open files"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-11-20
Cheers,

I am using uTorrent in wine as my BitTorrent Client, now I am getting an error "Too many open files", is this a uTorrent issue or a Ubuntu issue.  I tried to post this on the uTorrent forums but I didn't get any answers, so I'm trying my luck here.

Any ideas?

Thanks in advanced.

---

### Post by hotbrainz on 2006-11-20
hey delphidude..... use "azureus", it is also a torrent downloader. Works like a charm. You dont have to use wine and go thru all thi frustration.

Hope this helps.
Cheers

---

### Post by taurus on 2006-11-20
Or deluge since it uses less system resources than azureus and if you are using KDE, then try ktorrent.

---

### Post by delphiguy on 2006-11-20
I have tried Azurues before and I am not happy with it at least on ubuntu Dapper, I havent tried kTorrent though.

---

### Post by taurus on 2006-11-20
You can also check out deluge if you wish...

[http://www.ubuntuforums.org/showthread.php?t=288936](http://www.ubuntuforums.org/showthread.php?t=288936)

---

### Post by delphiguy on 2006-11-20
I have to add that I have never encountered this error with uTorrent while I was using Ubuntu Dapper.

---

### Post by zachtib on 2006-11-28
> **taurus said:**
> You can also check out deluge if you wish...

[http://www.ubuntuforums.org/showthread.php?t=288936](http://www.ubuntuforums.org/showthread.php?t=288936)

link to the deluge homepage or the subforum itself, as 0.3 is actually out of date now.

[http://deluge-torrent.org](http://deluge-torrent.org)

But still, thanks for the free advertising :)

---

### Post by taurus on 2006-11-28
> **zachtib said:**
> link to the deluge homepage or the subforum itself, as 0.3 is actually out of date now.

[http://deluge-torrent.org](http://deluge-torrent.org)

But still, thanks for the free advertising :)
Trying to help anyway I can.  ;)

---

### Post by catfishy on 2007-04-26
I've received this error several times when trying to add a torrent for 12 gb to the 80 or so that are already in utorrent.  It's an OS issue.  Here's what Demonoid says:

Unless configured otherwise some clients will keep all the files in a torrent open during the downloading process. This error occurs with some of the larger multi-file torrents, which can have hundreds or thousands of component files. When the number exceeds the OS limit, the OS refuses to allow them all to be opened, preventing the client from accessing them. To resolve the problem either   limit the number of files the client will have open at any one time or increase the OS limit for the number of open files.

Here is your solution:
hxxp://forum.utorrent.com/viewtopic.php?pid=225440   (i won't hotlink)

That worked for me today.....

---

### Post by schumifer on 2007-08-25
Just wanted to say thanks. I am also going to be trying out deluge

---

### Post by brucewagner on 2008-01-22
According to one (so-called) "Administrator" at the uTorrent forum....   (a forum I do NOT recommend, by the way - since it is run by mean children)

"This has been fixed in 1.8. File handles are closed immediately after it's done checking the file."

Unfortunately, version 1.8 apparently is still not released... or is still not "stable".

I wonder if uTorrent will ever create a version for Ubuntu....

I'd also love to hear from those of you who have already used ALL of the available bittorrent clients in Unbuntu....

[LIST]
[*]uTorrent under Wine
[*]Deluge
[*]Azureus
[*]Gutsy's "built-in" BitTorrent client
[*]Other
[/LIST]

If you've tried them all, please tell us:   Which one is best?   Why?   What do you like the best about each one?   What do you like least about each one?

Which one(s) are "supported", or officially "recommended", by Ubuntu...?

---

### Post by KrystoferRobin on 2008-06-23
I have tried...
Azureus - Longest load time, highest memory usage, and has a tendancy to close itself randomly.
uTorrent - Absolutely fabulous torrent management, especially if you're a dedicated seeder.  The scheduling is simple and powerful, you can tag your torrents to better sort them, and I seem to get the best overall speed averages out of it.  Loads fast, stays up without troubles, and doesn't slow my PC down.
KTorrent - Almost as good as uTorrent, but some of the options are a bit more difficult to find, and surprisingly it takes LONGER to load up than uTorrent does.
Opera's inbuilt torrent handler - It works, but for anything beyond a hit-and-run, its useless.
Deluge - Disliked the interface, couldn't get the scheduling or queuing to behave as expected.
and the default included with gutsy - Basic torrent manager, works fine, but lacks a lot of the advanced features of KTorent and uTorrent.

uTorrent was the fastest, and overall best for me.

To solve the "too many open files" you can...
sudo nano /etc/security/limits.conf

add this line (no <>'s)..

<your username>  hard nofile 4096

Unless you're dealing with a simply SICK amount of files, that should do the trick nicely.  I would have prefered some better way of dealing with this issue, but it works, and I get the benefit of the best torrent manager around, hands down.

---

### Post by alecz20 on 2008-06-24
I use uTorrent under Wine, and I was able to solve these problems.

With the new Wine, if uTorrent looks fabulous. 

I had the error "Too many open files", and i solved it by editing the /etc/security/limits.conf

I don't remember what I did to it, but I can look at it when I get home if anyone is interested.

uTorrent seems like the best client for me.

---

