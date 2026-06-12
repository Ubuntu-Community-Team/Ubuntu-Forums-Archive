---
title: "DNS problems"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-01-02
is what my roommate and I have determined I have.  Every couple hours, for five minutes or so, my internet connection seems to just go away.  Any downloads I have going continue unabated, and I can navigate within a domain that I'm already in, but if I try to open a new tab or go from, say, slashdot.org to science.slashdot.org, I hang at *looking up science.slashdot.org...*  My roommate said it was a DNS problem, which I guess makes sense.  I am vaguely aware of what DNS is, but only vaguely.  I don't really know where to start sorting this out.

Anybody had to deal with this out there?  Any ideas appreciated, as always.  -p.

---

### Post by bluefrog on 2006-01-02
are you on wifi? could be a bad connection.

if you are getting on the internet you have dns resolution, you may want to put more dns (given by your provider) in /etc/resolv.conf.

james

---

### Post by TeeAhr1 on 2006-01-03
Fishy.  I make a change to the file, save it, and it doesn't keep.  Next time I open the file, the old entries are there.  Ditto if I do it through System > Admin >Network.  Fishy indeed.  Anyone know what's up with this?

---

### Post by patholio on 2006-01-03
Hi, i had the same sorta problem, this fixed it...
[http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf]("http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf")

:)

---

### Post by proventech on 2006-01-03
what kind of internet connection do you have?  are you using a router?  have you tried another computer?

---

### Post by TeeAhr1 on 2006-01-03
Sweet!  That cut right through it.  Thanks!

---

