---
title: "opera 9 does not work"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-07-15
after dealing with update connectivity issues i succeeded in getting tthe opera 9 installed.
but when i launch it, it just showed first run and nothing happens...
unable to browse yet.
no proxy issues now as i connectt with statis ip now, no firewall. 
i can browse with firefox , no problem!
any ideas?:-k

---

### Post by catlett on 2006-07-15
Did you install it through the repositories? If you did it through the opera repository it should work without an isue.
Try uninstalling and then reinstalling for starters. The repository version has been installing and running without a problem.

---

### Post by drtvasudevan on 2006-07-15
oh, did install from the repo

---

### Post by T700 on 2006-07-15
> **drtvasudevan said:**
> 
but when i launch it, it just showed first run and nothing happens...


Not real clear what you mean.  Does the application launch and open, but you can not load any pages from the internet?

In Opera, go to Tools, Preferences, Advanced, Network, Proxy and make sure you do not have a proxy set.

Paul

---

### Post by drtvasudevan on 2006-07-16
that is right.the application launches.
showed first run ... and hung.
unable to browse any other site.
i guess one needs to run that first run which has not happened.
have tried that a few times.

no proxies. sure.

tv

---

### Post by T700 on 2006-07-16
If it is hanging and not fully launching, you might try restarting your window manager session (or just reboot, whichever is easier).  There could be a stalled instance of the Opera lurking in the background.

Paul

ps.  You could check for and kill the rogue process, but I'm suggesting the lazy way of doing it.

---

### Post by drtvasudevan on 2006-07-16
the installation was done yesterday.
there have been so many shutdowns and restarts.
no go.
:confused:

---

### Post by drtvasudevan on 2006-07-16
reinstalled and still no go

---

### Post by drtvasudevan on 2006-07-16
may be something from the previous attempts at installation from a deb package (never got it going anyway) is interfering.
how do i remove all the related files?

---

### Post by Colonel Kilkenny on 2006-07-16
Maybe you should try to run it from console.
Just write opera<enter> and see if it says anything unusual about errors.

"sudo aptitude purge opera" removes opera (and your opera configs, bookmarks etc.)

---

### Post by drtvasudevan on 2006-07-17
this is carzy,promise me not to laugh, ok?
after doing purge opera i tried install opera and the usual story began.
can launch but no browsing.
had a carzy idea and copied the url (first run) and pasted in the firefox box
i saw the home page of opera clicked another link and closed.
then switched to opera which was still running and ...
aamzing ! saw the link that opened from the home page of opera open! then i could click on and browse.
now i have tried closing and restarting.
it seems to work!

---

