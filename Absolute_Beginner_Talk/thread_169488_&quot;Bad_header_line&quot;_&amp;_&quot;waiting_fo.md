---
title: "&quot;Bad header line&quot; &amp; &quot;waiting for headers&quot;"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-05-02
I've got a bad problem...

I was downloading KDE, all the artwork and the optional stuff.
My computer crashed in the middle, something with the cable...

Anyway, I wanted to start again, so I went into the terminal,
sudo apt-get install kde
alright, it said I need to download 14MB of the 148 it is, i already downloaded the rest, fine. I did it, but it said 
> bad header line
after that > waiting for headers
and then it did nothing, stuck.

I guess it's because i've already downloaded part of it, and stopped in the middle, but I don't know how to fix it, I don't care if I have to start over, but this is buggering...

it's not the first time it happened, but last time it was with smaller application I could do without, so I didn't bother asking...

anything I can do?
thanks,
Josh:)

---

### Post by Caligula on 2006-05-02
well, the problem changed...
suddenly it started working, after a few minutes, 
but it gives me that error message, still something with bad header line.

> Need to get 2270kB/144MB of archives.
After unpacking 428MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe kdevelop3-data 4:3.2.3-0ubuntu1
  Bad header line [IP: 85.133.25.8 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/k/kdevelop3/kdevelop3-data_3.2.3-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/k/kdevelop3/kdevelop3-data_3.2.3-0ubuntu1_all.deb)  Bad header line [IP: 85.133.25.8 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

And it's not a problem with the server, because I went there manually and it's all there...
I tried downloading it there, but it came up with a different error, something that it's not in my PATH, what is it?

---

### Post by Caligula on 2006-05-02
it's alright, solved itself...
but my cable is really bad, means my computer crashes a lot, will it cause problems if it crashed during the installation of the packages?

thanks

---

### Post by halfvolle melk on 2006-05-02
Try something like
```
sudo apt-get install -f
```
I can't remember for sure how this works, but the above doesn't return any syntax errors. This is what man says about -f or --fix-broken
> Fix;  attempt  to  correct  a system with broken dependencies in place. This option, when used with install/remove, can omit  any packages  to permit APT to deduce a likely solution.
Hope this helps but I'm not at all sure.

edit: ok, that's always nice, problems that fix themselves :). What cable are you refering to?

---

