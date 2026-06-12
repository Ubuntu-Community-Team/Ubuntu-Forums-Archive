---
title: "Internet Seems Slower"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-06-22
A few weeks ago I purchased a wired Linksys BEFSR41 router.  Since then, I've noticed that my internet speed has become noticeably slower.  It's not that it's loading the web pages at a slower speed, it just seems to take longer to *begin* loading them, if that makes any sense.  When the computer is plugged directly into the modem it appears to connect to the webpage immediately, but with the router in between it takes several seconds.  I use Opera, and it clearly states at what speed it's dl'ing (at 0 kb/s for the first few secs, and then up to 60+).  Is this a configuration problem with Xubuntu - I had to manually configure the internet to work when I first installed the ethernet PCI card in the computer - or is this a normal characteristic of routers (I've never owned a router before), or do I perhaps need to update firmware in the router to solve the problem?  The same result is happening on my XP computer, but not to the same degree, and I don't know if that computer needs configuration as well, or what.  I'm so confused and miss my lightening fast internet speed, but can't give up my new ability to connect on two computers at once.  Please help.  Much thanks.

---

### Post by jvl on 2006-06-22
What's in your /etc/resolv.conf ?

what is the 'time host www.ubuntu.com' command's output?

mine is:
$ time host [www.ubuntu.com](www.ubuntu.com)
[www.ubuntu.com](www.ubuntu.com) has address 82.211.81.166

real    0m0.077s
user    0m0.010s
sys     0m0.000s

---

