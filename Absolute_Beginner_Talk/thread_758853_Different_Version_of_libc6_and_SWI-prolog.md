---
title: "Different Version of libc6 and SWI-prolog"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by joecommon6758 on 2008-04-18
Hey, 

I am trying to use the PDT plugin for eclipse ([https://sewiki.iai.uni-bonn.de/research/pdt/users/download](https://sewiki.iai.uni-bonn.de/research/pdt/users/download)) and encountered some problems.

By now i think that I just need newer versions of libc6, XPCE and swi prolog.
Using the normal synaptic i got libc6 version 2.6.1-lubuntu10, XPCE 6.6.14 and swi prolog 5.6.14.

I need libc6 2.7-10ubuntu3, swi-prolog 5.6.52-1 and swi-prolog-xpce
5.6.52-1.

Is there any 'nice' way to install them or do I have to do it manually (download, extract, copy) ?

thanks, 
joe

---

### Post by unutbu on 2008-04-18
Don't know much about eclipse or PDT, but I did notice that the link you referenced 
is to sewiki.iai.uni-bonn.de instead of eclipse.org, and its download is dated 2006-11-xx, while 

[http://download.eclipse.org/tools/pdt/downloads/index.php](http://download.eclipse.org/tools/pdt/downloads/index.php)

has a stable relase with a build date of 2007-12-xx. I don't know if this is the same thing but I thought I'd mention it...

Also 
[http://www.thierryb.net/pdtwiki/index.php?title=Using_PDT_:_Installation_:_Installing_PDT](http://www.thierryb.net/pdtwiki/index.php?title=Using_PDT_:_Installation_:_Installing_PDT)

seems to give instruction on how to install.

---

### Post by joecommon6758 on 2008-04-19
Thanks for your advice, 

Seems like there are at least two PDT plugins for Eclipse out there.
The link I gave (sewiki.iai.uni-bonn.de) is the homepage for the Prolog Developtment Tool
plugin for Eclipse. Yes, it is kinda outdated, but the mailinglist is still active. :-)

When I tried to run PDT I got some errors. I asked the mailinglist for help and we think that all I need to do update libc6 and swi-prolog.
apt-get doesn't work (think they are unstalble) and I don't really know how else to do it.

---

### Post by joshrobinson on 2008-04-19
im running hardy heron
it has

libc6 2.7-10ubuntu3
swi-prolog 5.6.47-1
swi-prolog-xpce 5.6.47-1

so it meets the lic6 requirement, but not the other 2, just thought i would throw that out there
hardy becomes official next week, upgrading to that might bring you close to your goal

---

### Post by unutbu on 2008-04-19
I think I have all the official repositories covered, and here are the results
```

% apt-cache policy swi-prolog-xpce
swi-prolog-xpce:
  Installed: (none)
  Candidate: **5.6.14-1**
  Version table:
     5.6.14-1 0
        500 http://archive.ubuntu.com gutsy/universe Packages
        500 http://us.archive.ubuntu.com gutsy/universe Packages

% apt-cache policy swi-prolog
? ([Y]/n/q) 
swi-prolog:
  Installed: (none)
  Candidate: **5.6.14-1**
  Version table:
     5.6.14-1 0
        500 http://archive.ubuntu.com gutsy/universe Packages
        500 http://us.archive.ubuntu.com gutsy/universe Packages

% apt-cache policy libc6
? ([Y]/n/q) 
libc6:
  Installed: **2.6.1-1ubuntu10**
  Candidate: 2.6.1-1ubuntu10
  Version table:
 *** 2.6.1-1ubuntu10 0
        500 http://archive.ubuntu.com gutsy-updates/main Packages
        100 /var/lib/dpkg/status
     2.6.1-1ubuntu9 0
        500 http://archive.ubuntu.com gutsy/main Packages

```

It looks like the official repositories (for Gutsy) do not have what you need.

---

### Post by mc4man on 2008-04-19
Your best bet if you really want this is to upgrade to hardy. While you could force a higher ver. of libc6 in gutsy it will cause you nothing but problems
Here are your other packages  (note dependencies )
[http://packages.debian.org/lenny/swi-prolog](http://packages.debian.org/lenny/swi-prolog)
[http://packages.debian.org/lenny/swi-prolog-xpce](http://packages.debian.org/lenny/swi-prolog-xpce)

---

### Post by joecommon6758 on 2008-04-20
Thanks a lot guys!

I upgraded to Hardy and was able to install all the packages (and learned about manual installing :-) ).

Unfortunately it still isn't working, but that's probably due to the actual PDT code. Gotta go back to the mailinglist.. 

again, thanks a lot for your help.

---

