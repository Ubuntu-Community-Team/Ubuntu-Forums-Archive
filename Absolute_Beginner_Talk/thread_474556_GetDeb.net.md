---
title: "GetDeb.net"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-15
Hi,

While i was searching in the forum on how to Install AlienArena because in the website as .tar.g2z file
so i found a site called [www.getdeb.net](www.getdeb.net)

I liked it very much, it gives you the .deb file for many applications and games

Althought the site is still new, i expect it to have a great future

Just wanted to inform you about it so you can also benefit from it

---

### Post by hyper_ch on 2007-06-15
yeah, it's a nice site... I've installed a few apps from there already :)

---

### Post by eentonig on 2007-06-15
Maybe a stupid question, but what's the added value in relation to the regular repositories?

---

### Post by Cappy on 2007-06-15
It has newer versions that are not in the repos (boinc, for instance). It also has a lot of applications that aren't in the repos (lots and lots of games!).

---

### Post by eentonig on 2007-06-15
Hmm, ok.

Newer versions are generally not my first concern. Stability is more to my liking. How about updates afterwards? Will these apps get automatic notifications if a new update is available?

Apps not in the repo's might be a compelling reason. But again, will you be notified of updates?

I'd rather prefer to see them hosting a repo (andperhaps optional web interface additionally).

---

### Post by bamesah on 2007-06-15
> **eentonig said:**
> Hmm, ok.

Newer versions are generally not my first concern. Stability is more to my liking. How about updates afterwards? Will these apps get automatic notifications if a new update is available?

Apps not in the repo's might be a compelling reason. But again, will you be notified of updates?

I'd rather prefer to see them hosting a repo (andperhaps optional web interface additionally).

I really don't know if they will get automatic updates or not, i didn't try that

---

### Post by Carlos Santiago on 2007-06-15
Yes, it has a lot of nice software that is not in repositories, most probably because they didn't pass the full stability tests.

My advice is to try software that is not in repositories, only if you really need it!

Two days ago I installed Referencer and Brikx from there, that also require several other packages. The problem is that now my system is very unstable! 

My PC now crashes in a way that not even a X restart (ctrl+alt+backspace) could repair. Only solution is to  reboot. 
Before installing software from here, I never had a problem of this severity! And it is much slower than before. 

Anyone PLZ know how could I remove all software and its dependencies that I installed from here?

Probably some dependencies were installed from the repositories, but as they were requested by these packages, I would also like to remove them.


Thanks in advance.


Carlos

---

### Post by Cappy on 2007-06-15
```
sudo dpkg --remove packagename
```
to remove it.

So it probably is
```
sudo dpkg --remove brikx
```

---

### Post by Carlos Santiago on 2007-06-15
Thankx Cappy.

Do you know if it also removes the dependencies?
That is my main question! 

I want to remove all dependencies installed by brikx.
As I didnt install anything after it, they should not be needed by any other package.

---

### Post by bamesah on 2007-06-16
> **Carlos Santiago said:**
> Thankx Cappy.

Do you know if it also removes the dependencies?
That is my main question! 

I want to remove all dependencies installed by brikx.
As I didnt install anything after it, they should not be needed by any other package.

I think that the only files are brix-data andbrix. Maybe you can remove each one of them as an individual package?

```
sudo dpkg --remove brikx
```   

```
sudo dpkg --remove brikx-data
```

Maybe that will work

---

### Post by Carlos Santiago on 2007-06-16
Thankx bamesah,
I clean up the unused dependencies with:
```
sudo apt-get autoremove
```

That was great, now everything is stable again ;-)

---

### Post by bamesah on 2007-06-16
Good to hear you got everything to normal again

---

