---
title: "Question about Ubuntu development"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by w3stfa11 on 2007-04-14
I have a few questions. :) 

1. What was the first official release that used launchpad? Was it used at the very beginning (4.10) or later?

2. What was the first official release that stopped using a text installer and used the Ubiquity installer by default?

3. First official release with >= GCC 4.0 by default?

4. First release to use ShipIt?

5. Did Ubuntu always support x86, x86-64, and PPC? If not, when did each become supported?

Thanks all. I appreciate it!

---

### Post by K.Mandla on 2007-04-14
I'm trying to scrape my memory on these, and I'm probably wrong on some, if not all of them. ...

1. Launchpad came about roughly a year ago (?), and [Bugzilla]("http://bugzilla.ubuntu.com/") was the old version. This one is called [Malone]("https://launchpad.net/malone") sometimes, but I don't recall why. 

2. I think Dapper had the first viable live CD installer. It might even have been one of the reasons for the delayed release. You can still get a text-based installer; I use it all the time.

3. I'm thinking [Breezy]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=gcc") had gcc-4.0, but I don't remember if it had it by default or if it was an upgrade. I think maybe it was an upgrade because I remember some things had to be recompiled to work under 4.0.

4. I think Hoary had the first Shipit CDs, but it might have been Breezy. My first Shipit CDs were Breezy. I don't think Warty had pressed CDs.

5. This one I'm not too sure on. I thought PPC was around from the start, but I think x86_64 was added around Breezy.

I'm sure some true old-timers will be able to correct me on these. I was very green when some of these things happened, so I might not have been paying attention. :roll:

---

### Post by John.Michael.Kane on 2007-04-14
1. What was the first official release that used launchpad? Was it used at the very beginning (4.10) or later?

That would be breezy badger 5.10

2. What was the first official release that stopped using a text installer and used the Ubiquity installer by default?

Dapper 6.06.1

3. First official release with >= GCC 4.0 by default?

Ubuntu breezy badger 5.10

4. First release to use Ship It?

Warty 

5. Did Ubuntu always support x86, x86-64, and PPC? If not, when did each become supported?

Ubuntu supported x86, x86-64, and PPC from warty on.

---

### Post by TravisNewman on 2007-04-14
5. And now support seems to be gradually dropping for PPC, and Playstation3 is now available. I can't recall when, but a few releases ago a SPARC release came out, but you couldn't get it via ship it

---

### Post by w3stfa11 on 2007-04-14
Thank you, SD-Plissken, for answering all my questions. Oh and  K.Mandla, you were mostly right. ;)

---

### Post by 23meg on 2007-04-14
> 1. What was the first official release that used launchpad? Was it used at the very beginning (4.10) or later?

All bug reporting was moved to Malone (Launchpad's bug tracking module) in January 2006; that was during the Dapper development period. A while before that, for a few months, only Universe bugs were reported to Malone, and bugs in main were still reported to the Bugzilla; they were joined in January.

> 3. First official release with >= GCC 4.0 by default?

Breezy (5.10), but its kernel was still compiled with gcc 3.4.

---

