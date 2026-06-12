---
title: "How To Get Swat To Work?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by antiwindows798 on 2007-02-06
I have installed Samba, SWAT, inted, etc. "Swat" was already uncommented in /etc/inetd.conf and yes, I have already done /etc/init.d/inetd restart but [http://localhost:901](http://localhost:901) STILL gives me a "page no found" error. I have also followed the instructions at [http://copia.ogbuji.net/blog/2006-01-26/The_madnes](http://copia.ogbuji.net/blog/2006-01-26/The_madnes) but SWAT still doesn't show up at [http://localhost:901](http://localhost:901).

Apparently, this is a common problem with Ubuntu and unsurprisingly, as usual, nobody seems to know the answer or does someone know how to get SWAT running?

---

### Post by ^rooker on 2007-02-06
A friend of mine has had similar problems with SWAT (using DevilLinux). [See solutions here]("http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=346&highlight=swat").

[And more here.]("http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=307&highlight=swat")

In both cases it was the "only_from       = localhost " line in /etc/xinetd.conf

---

### Post by antiwindows798 on 2007-02-07
Doesn't work

---

### Post by ihatecommies on 2007-02-07
Doesn't SWAT need a webserver for that?

---

