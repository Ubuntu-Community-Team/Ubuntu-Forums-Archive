---
title: "Any initial advice re creating intranet server?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by nrpgeek on 2007-07-11
Hi Folks,

1st post on forum so patience please - thanks!

Installed Ubuntu fine - really impressed (if a little unfamiliar).

I'd like to use Ubuntu as an intranet server and eventually as an internet server (will probably use the server version for that)

Any pointers?

PS. Used computers for nearly 30 years, but only 2 days on Linux!

---

### Post by Qwerty_ on 2007-07-11
Well I assume you are going to want to run apache so first port of call would be to check here.

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by hyper_ch on 2007-07-11
if you just want a pure server, I'd head for Debian instead.... however if you want a desktop and a server then stick with ubuntu...

For making a ISP-style setup (e.g. host multiple websites independantly of each other) have a look at the howtos at [http://www.howtoforge.com](http://www.howtoforge.com) --> they have very good information on how to setup webservers.

---

### Post by nrpgeek on 2007-07-11
Thanks for that folks, that's the next steps sorted.

I had looked in the 'Applications|Add/Remove' list and Apache was not there, so - being Linux falsely assumed it was part of the install. Started to get suspicious when I couldn't find inetpub or any other physical manifestation of local host.

I suppose my next decision is whether to install Apache on present system, or to install the server version with LAMP.

One more question (if I may be cheeky?)...

Does the server version come with the desktop/gui similar to the present version?

---

### Post by hyper_ch on 2007-07-11
A server should not have any gui...

In linux all configuration is done through files. There's not really a gui needed and loading a gui uses ressources that are better used on the server for delivering its services...

But then, it depends what you want... if you want to really setup a server then you don't need a gui... if you want to work also on it, then you first install normally the desktop-cd or alternate one and add the servers later...

---

### Post by nrpgeek on 2007-07-11
THanks for the link - it looks like exactly what I need!

---

### Post by nrpgeek on 2007-07-11
A server should not have any gui...

In linux all configuration is done through files. There's not really a gui needed and loading a gui uses ressources that are better used on the server for delivering its services...

..

Many thanks... 

It's becoming clearer now - bit of a culture shock after years of Micro$oft! That explains why the server ISO is smaller than the desktop version.

---

### Post by az on 2007-07-11
> **nrpgeek said:**
> 
It's becoming clearer now - bit of a culture shock after years of Micro$oft! That explains why the server ISO is smaller than the desktop version.

Go ahead and install the LAMP packages on your desktop - they will work fine.  You can play around and see how things work.  Once you are ready to put it online, you can use the server disk to reinstall your system as server-only.

---

### Post by nrpgeek on 2007-07-11
Getting the hang of it now - thanks az, hyper, querty. I've had a poke around and az has confirmed my next step. Installing the LAMP packages is tonights project, then get a simple intranet running.

The next step is to get used to all the terminal commands and switches and all the various files. The help is all out there though - I'm bookmarking it as I find it.

Many, many thanks again guys - really grateful!

---

### Post by hyper_ch on 2007-07-11
Terminal commands aren't that hard....

and don't underestimate the power of the man pages :)

If you run anything in the command line it also has man pages.

e.g. copy is done by the "cp" command... to see how to use cp you just enter:

```

man cp

```

and you have the man pages there... sometimes there's just too much information in there ;)

If you encounter problems, just ask here :)

---

### Post by nrpgeek on 2007-07-11
Once more - thanks hyper.

When I first started looking at this a couple of days ago, I was beginning to think I'm getting too old... etc, etc

I'm starting to see new stuff already that's transferable ***back*** to the Micro$oft environment (which I've worked in for too long!!!). I'm not too old, just haven't learned anything too new for too long. Seems I got here just in time!

---

