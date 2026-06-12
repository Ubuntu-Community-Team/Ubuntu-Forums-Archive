---
title: "[SOLVED] pleeease help me set up wget properly.."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-23
Hi,

Can you help me set up a wget properly?

i want to download a .asp web site forum and periodically check for updates

i only download pages starting with
/forum.asp?FORUM_ID=*
/forum/topic.asp?TOPIC_ID=*
and all images associated
be able to view offline
convert to .html
and ignore these forums:
FORUM_ID=11,34,44,51,53,5,57,6,7
ignore 1 link on the default.asp
[https://www.website.com/jusx/files/login.asp](https://www.website.com/jusx/files/login.asp)

i got so far:

**wget -S -L --accept topic.asp?TOPIC_ID=*,forum.asp?FORUM_ID=*,default.asp --wait=20 --limit-rate=20K -r -p -U Mozilla --mirror --load-cookies ~/.mozilla/firefox/xjg5nmlx.default/cookies.txt [http://www.website.com/forum/default.asp](http://www.website.com/forum/default.asp)**

the above wget [COLOR="Red"]does not follow links[/COLOR] at all...

I have no idea what i'm doing by the way :)

Thanks..

---

### Post by Hopeless on 2007-08-23
*bump*

i always get this too...
[COLOR="Red"]Last-modified header missing -- time-stamps turned off.[/COLOR]

how come? the bits in red? anyway to fix it?

Many thanks...

---

### Post by Hopeless on 2007-08-23
*bump*

---

### Post by Hopeless on 2007-08-26
*bump*

why doesn't wget follow links on the page and downloads one page only?

Thanks

:popcorn:

---

### Post by kwacka on 2007-08-26
doesn't -l1 set it to one level, -2 to 2 levels, etc?  So, -l5 would take it down to 5 levels i.e. downloads links on the page, links on those links, and so on. (You'll get a full ahtddrive pretty quickly).

Also check out the -r option.

---

### Post by Hopeless on 2007-08-26
-mirror is supposed to recursive all levels...tried your suggestion...

```
shane@lotus:~$ wget -Lp  -l1 --accept topic.asp?TOPIC_ID=*,forum.asp?FORUM_ID=*,forum.asp --wait=20 --limit-rate=20K -U Mozilla --mirror --html-extension --load-cookies ~/.mozilla/firefox/xjg5nmlx.default/cookies.txt http://www.website.coms/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1
[1] 5945
[2] 5946
[3] 5947
shane@lotus:~$ --21:11:00--  http://www.website.com/forum/forum.asp?FORUM_ID=35
           => `www.website.com/forum/forum.asp?FORUM_ID=35'

HTTP request sent, awaiting response... 200 OK
Length: 108,768 (106K) [text/html]

100%[====================================>] 108,768       20.00K/s    ETA 00:00

Last-modified header missing -- time-stamps turned off.
21:11:07 (19.98 KB/s) - `www.website.com/forum/forum.asp?FORUM_ID=35.html' saved [108768/108768]

Loading robots.txt; please ignore errors.
--21:11:27--  http://www.website.com/robots.txt
           => `www.website.com/robots.txt'
Reusing existing connection to www.website.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 26 [text/plain]
Server file no newer than local file `www.website.com/robots.txt' -- not retrieving.


FINISHED --21:11:27--
Downloaded: 108,768 bytes in 1 files

```

nothing..

Any ideas on whats doing this?

---

### Post by Hopeless on 2007-08-26
*
B
U
M
P
*

---

### Post by Hopeless on 2007-08-27
*bump de la bump*

does anyone know why wget can't follow links?

where else can i get wget help from? any other forums you know of?

thanks...

---

### Post by Hopeless on 2007-08-27
can't use ????? in wget...

---

### Post by lemurian on 2007-08-30
What was your solution?

I ran into a similar problem.  In my case I had to specify "-e robots=off".

---

