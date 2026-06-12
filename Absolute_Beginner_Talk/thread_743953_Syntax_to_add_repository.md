---
title: "Syntax to add repository?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by von Stalhein on 2008-04-03
Well, I just found out about FlightGear, and I then checked Synaptic and found it's in the package manager at version 0.9.102Ubuntu2 
I'm using 7.10

Knowing that there was a newer version of FlightGear out, I went to [http://packages.debian.org/sid/i386/flightgear/download]("http://packages.debian.org/sid/i386/flightgear/download") to get it. Noticing the instructions about adding it to the package manager rather than downloading it, I had a crack.

Below is what I put into the sources.list. file.

```
# FlightGear open source flight simulator
deb http://ftp.au.debian.org/debian/pool/main/f/flightgear/
```

I keep getting an error message when I open Synaptic

```
E: Malformed line 46 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report. 
```

As a relative Ubuntu n00b, can someone tell me what's wrong in my syntax please?

thanks   :)

BTW, I posted this in the games forum, but I think the relevant thread is dead, as it's been 2 days. I absolutely abhor cross-posting, so I apologise if this upsets anyone :redface:

---

### Post by kellemes on 2008-04-03
It probably should be something like this..
```
deb http://ftp.au.debian.org/debian sid main
```

By the way, [getdeb has it too]("http://www.getdeb.net/search.php?keywords=flightgear")

How to manage repositories..
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by PeterJS on 2008-04-03
From the page you linked to the full repository description is:
```

deb http://ftp.de.debian.org/debian sid main 

```

But you really don't want to add the entire debian sid main component to your system. The sid core system packages are definately newer than the ones in gutsy and will overwrite/"update" packages that it really shouldn't. Your best bet would be to download the standalone deb from the mirrors below and install that.

---

### Post by von Stalhein on 2008-04-03
Thanks very much for the quick replies.

OK, on balance I might go with the actual d/l of the .deb to avoid any other issues.

I suppose the thing that annoyed me most was stuffing up the sources syntax, but I see what I did there.

---

