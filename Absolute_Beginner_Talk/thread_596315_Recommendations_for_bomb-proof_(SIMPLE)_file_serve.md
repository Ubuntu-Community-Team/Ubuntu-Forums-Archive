---
title: "Recommendations for bomb-proof (SIMPLE) file server?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by teastman on 2007-10-29
Hi folks.

Sort of new to linux.  I've had three linux installs on my machine at home SuSE7.3, 9.1 and Kubuntu 7.4 (which I really like and use now)

Question is this - we are running out of space here at work and I want to build a Linux raid5 server which will basically share with a Windows 2003 Small Business Server environment.  All it has to do is share files.  It won't be a print server or Proxy server or mail server.

Just share files efficiently over a windows network of 18 users.

I have looked at OpenFiles 2.2 at [http://www.openfiler.com/](http://www.openfiler.com/) which is basically a NAS install but I am unfamiliar with that distro (derived from rPath Linux)

So I need a streamlined server install which can boot itself up to it's network share state, and talk easily with a UPS.

Is there a whitesheet somewhere explaining this?

Thanks!

---

### Post by borris.morris on 2007-10-29
this one is pretty good : [http://http://www.serverelements.com/naslite.php]("http://http://www.serverelements.com/naslite.php")

---

### Post by teastman on 2007-10-29
NASlite does not appear to support joining a Windo$e SBS domain.  This will be required i think.

---

### Post by borris.morris on 2007-10-30
Oh, ok. I saw a really good one like NASlite, but I can't seem to find it anymore. It was simply amazing! I'll look for it though....
Found it. [www.freenas.org](www.freenas.org)
or [www.openfiler.com](www.openfiler.com)

---

