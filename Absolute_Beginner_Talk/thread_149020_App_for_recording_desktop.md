---
title: "App for recording desktop"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Klejs on 2006-03-23
Hi all, 

I want to be able to record my games and applications like you can do in the program **Fraps** under Windows. I just wanted to ask you guys if there are
any apps similar to this for GNU/Linux??

---

### Post by louis_nichols on 2006-04-15
well... if I understand your question well, then you need xvidcap or gvidcap (it's actually the same app, coming in one package, just has 2 GUI's). So, if you've enabled all repos, it should install nicelly with

$sudo apt-get install xvidcap

---

### Post by towsonu2003 on 2006-04-15
may be sudo apt-get install istanbul
?

---

### Post by trent dillman on 2006-04-15
is xvidcap in the repos?

[http://ubuntuforums.org/showpost.php?p=859571&postcount=10](http://ubuntuforums.org/showpost.php?p=859571&postcount=10)

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=trent dillman]is xvidcap in the repos?

[http://ubuntuforums.org/showpost.php?p=859571&postcount=10](http://ubuntuforums.org/showpost.php?p=859571&postcount=10)[/QUOTE]
I think not: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xvidcap&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xvidcap&searchon=names&subword=1&version=breezy&release=all)

but it's not a typo I guess: xvidcap.sourceforge.net

try istanbul first (easier to install) I guess? I'm not sure if it record sound. hmmm, let me try :)

edit: wow, it's a cpu killer, be careful. I was expecting better performance from something named istanbul :(

---

### Post by towsonu2003 on 2006-04-15
I just tried istanbul... Let me just say: try xvidcap instead.... It was so bad, I even filed a bug for this...

---

### Post by louis_nichols on 2006-04-16
xvidcap is in the repos. just make sure you activate universe and multiverse (I don't know exactly in which one of them it is. Alternatelly, go here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

and build yourself a customized sources.list.

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=louis_nichols]xvidcap is in the repos. just make sure you activate universe and multiverse (I don't know exactly in which one of them it is. Alternatelly, go here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

and build yourself a customized sources.list.[/QUOTE]
I guess it's in backports.

---

### Post by louis_nichols on 2006-04-16
Perhaps it's in one of the extra repos I got using source-o-matic. This is output from my console:

```
myself@home:/$ apt-cache search xvidcap
xvidcap - xvidcap X to video capture utility

```

But I realize now I don't know how to find out which repo a package comes from. :))

Anyways, using source-o-matic directly is a petty good idea. I enabled everything there, cauze I like to have where to choose from.

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=louis_nichols]Perhaps it's in one of the extra repos I got using source-o-matic. This is output from my console:

```
myself@home:/$ apt-cache search xvidcap
xvidcap - xvidcap X to video capture utility

```

But I realize now I don't know how to find out which repo a package comes from. :))

Anyways, using source-o-matic directly is a petty good idea. I enabled everything there, cauze I like to have where to choose from.[/QUOTE]
try this one: 
apt-cache show xvidcap | grep Section

PS. I'm pretty sure the OP has left, anyway I like this stuff (i.e. I'm learning).

---

### Post by louis_nichols on 2006-04-16
here's the output:
```
myself@home:~/downloads$ apt-cache show xvidcap | grep Section
Section: extra

```

I guess it isn't all that helpful... Sorry! Did you try source-o-matic?

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=louis_nichols]here's the output:
```
myself@home:~/downloads$ apt-cache show xvidcap | grep Section
Section: extra

```
I would think it was gonna say "multiverse" or "universe" or "backports". Anyway. I found this:
[https://launchpad.net/distros/ubuntu/breezy/+source/xvidcap](https://launchpad.net/distros/ubuntu/breezy/+source/xvidcap)
which is the source. this may be the reason: I don't have source repos enabled. I guess the op will have to enable multiverse source repository to get this. 

In these mirrors, there is no .deb either:
[http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/x/xvidcap/](http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/x/xvidcap/)
[http://godel.cs.bilgi.edu.tr/ubuntu/pool/multiverse/x/xvidcap/](http://godel.cs.bilgi.edu.tr/ubuntu/pool/multiverse/x/xvidcap/)
[http://ftp.ale.org/pub/mirrors/ubuntu/pool/multiverse/x/xvidcap/](http://ftp.ale.org/pub/mirrors/ubuntu/pool/multiverse/x/xvidcap/)

Also found an old thread where xvidcap was requested but rejected (warty?) bc it didn't build or something... 
[QUOTE=louis_nichols]Did you try source-o-matic?[/QUOTE]
Believe it or not, I'm not trying to install this. Just trying to help the OP, who seems to have left long ago [-( :P I guess this much should be enough to help the OP?

---

### Post by louis_nichols on 2006-04-16
well... what you are writing is pretty strange... Where did I get this package? I know it wasn't built by me, cause it has dependencies and all, whereas I build debs with checkinstall and don't bother with deps.

well, here is a package that seems to have appeared out of nowhere! :)

well, if the OP wants it... the best thing I can advise (sorry about having to repeat myself) is to build a repo list at source-o-matic and use it. xvidcap has GOT to be somewhere in there. :D

---

### Post by stoeptegel on 2006-04-16
[QUOTE=louis_nichols]
But I realize now I don't know how to find out which repo a package comes from. :))
[/QUOTE]

aptitude show packagename should show you a
Section: i.e. universe/kde

---

### Post by louis_nichols on 2006-04-17
[QUOTE=stoeptegel]aptitude show packagename should show you a
Section: i.e. universe/kde[/QUOTE]

sorry :(

```
myself@home:/$ aptitude show xvidcap
Package: xvidcap
New: yes
State: installed
Automatically installed: no
Version: 1.1.3-1
Priority: extra
Section: extra
Maintainer: karl.h.beckers@gmx.net
Uncompressed Size: 4175k
Description: xvidcap X to video capture utility
 This little tool captures X action and saves it to individual frames or an
 encoded video stream

myself@home:/$
```

isn't this strange? To have a package on your pc and have no idea where it comes from? looool

---

### Post by towsonu2003 on 2006-04-17
maybe you built it from source using apt-get? (apt-get can build from source when src is enabled and told to do so)

---

### Post by louis_nichols on 2006-04-17
I've only used that once, to solve a bug in krusader. It's definitely binary, from somewhere.
I guess it's possible I found the deb somewhere and installed it, then deleted it...

---

### Post by lazyd2 on 2006-04-17
Here's the repository

deb [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/) stable main

---

### Post by towsonu2003 on 2006-04-17
\\:d/

---

