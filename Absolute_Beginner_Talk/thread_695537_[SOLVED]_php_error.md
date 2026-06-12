---
title: "[SOLVED] php error"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by japephillips on 2008-02-13
I am getting the below message and variants when browsing to a regular website, I think it is their end but others on Win machines are browsing there OK still (checked by email), Any ideas? Using latest Firefox and 7.10


phpBB : Critical Error

Error doing DB query userdata row fetch

DEBUG MODE

SQL Error : 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 6

SELECT u.* FROM phpbb_users u, phpbb_sessions_keys k WHERE snip

---

### Post by kesman on 2008-02-13
It's a problem in the site, not in your browser. Maybe paste the address here to get more opinions. If your friends are using internet explorer or something NOT firefox, advice them to clean the cache of the browser to force loading the site.

---

### Post by japephillips on 2008-02-13
[http://www.ozbow.net/ozbow_v2_001.htm](http://www.ozbow.net/ozbow_v2_001.htm)

I will be really interested to see what you get. the links I cannot get are to threads and 'campfires'. I have cleared my cache, tried with scripts and cookies allowed and disallowed and i still get the error. The front page part loads only and most of the links go to a script error. i can browse elsewhere (here and now for example) with no errors

here's the rub ... I setup an old box this morning using XP and IE and had absolutely no problems, so came back to this linux machine, re-installed Firefox, still can't get that site.

---

### Post by LaRoza on 2008-02-13
> **japephillips said:**
> [http://www.ozbow.net/ozbow_v2_001.htm](http://www.ozbow.net/ozbow_v2_001.htm)

I will be really interested to see what you get. the links I cannot get are to threads and 'campfires'. I have cleared my cache, tried with scripts and cookies allowed and disallowed and i still get the error. The front page part loads only and most of the links go to a script error. i can browse elsewhere (here and now for example) with no errors


Campfires: [http://www.ozbow.net/phpbb2/](http://www.ozbow.net/phpbb2/) 

I can read the threads fine.

(Ubuntu 7.10, Opera 9.50b)

---

### Post by japephillips on 2008-02-13
thanks LaRoza, i notice you use Opera, well I re-installed Firefox and all the dependencies and got the same errors. I am sure it is Firefox, got the same probs in two installations despite everything i tried.

so I gave up and installed Opera, it is fast and WORKING:guitar:

so partly solved ...if Firefox f****s up, go to Opera

---

### Post by emarkd on 2008-02-13
Opera's a fine browser, but it's not Firefox causing the trouble.  I can see the forum fine with Firefox.

PHP script is executed on the server, so I think the site was just having issues for a bit.

---

### Post by japephillips on 2008-02-13
well, i have used Firefox since its beginning in XP so i spent ages loading it up with noscript and various other addons in Linux but it became slow and unwieldy. this latest prob was the last blow so to speak. I still do not understand then if they were server problems why IE was fine, Galeon was fine until it locked up, Opera is fine, but Firefox 2 and 3 were not? Not to worry, i shall stick to Opera until it stuffs up, thanks

---

